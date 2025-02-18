---
title: Retrieve Target activities - Migrate from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension
description: Learn how to retrieve Adobe Target activities when migrating from the Adobe Target to the Adobe Journey Optimizer - Decisioning Mobile extension.
exl-id: 39569088-a254-4e64-9956-0c6e1a8ed2a5
---
# Retrieve Target activities 

Target mobile implementations use regional mboxes (now known as "scopes") to deliver content from activities that use Target's form-based Experience Composer. You need to update your mobile application to include scopes in your network calls.

The content returned by Target, also known as "offers", typically consists of text or json which you need to consume in your application to render the final customer experience. Offers from Target are often used to:

* Enable feature flags in your application
* Serve alternate text or images

If you have activities which need to run in both Target extension and Decisioning extension versions of your application, be sure to test thoroughly. If you need to use different offers for different versions of your app, consider using the targeting options in the interface to deliver different offers to the different versions.

Always be sure to include error handling to display suitable experiences under error conditions.


## Request and apply content on demand

+++ Android example

>[!BEGINTABS]

>[!TAB Optimize SDK] 

```Java

// Mboxes for Target activities
final DecisionScope decisionScope1 = DecisionScope("myTargetMbox1");
final DecisionScope decisionScope2 = new DecisionScope("myTargetMbox2");
 
final List<DecisionScope> decisionScopes = new ArrayList<>();
decisionScopes.add(decisionScope1);
decisionScopes.add(decisionScope2);
 
// Prefetch the Target mboxes
Optimize.updatePropositions(decisionScopes,
                            new HashMap<String, Object>() {
                                {
                                    put("xdmKey", "xdmValue");
                                }
                            },
                            new HashMap<String, Object>() {
                                {
                                    put("dataKey", "dataValue");
                                }
                            },
                            new AdobeCallbackWithOptimizeError<Map<DecisionScope, OptimizeProposition>>() {
                                @Override
                                public void fail(AEPOptimizeError optimizeError) {
                                    // Log in case of error
                                    Log.d("Target Prefetch error", optimizeError.title);
                                }
 
                                @Override
                                public void call(Map<DecisionScope, OptimizeProposition> propositionsMap) {
                                    // Retrieve cached propositions if prefetch succeeds
                                    Optimize.getPropositions(scopes, new AdobeCallbackWithError<Map<DecisionScope, OptimizeProposition>>() {
                                        @Override
                                      public void fail(final AdobeError adobeError) {
                                              // handle error
                                        }
 
                                        @Override
                                        public void call(Map<DecisionScope, OptimizeProposition> propositionsMap) {
                                              if (propositionsMap != null && !propositionsMap.isEmpty()) {
                                                // get the propositions for the given decision scopes
                                                if (propositionsMap.contains(decisionScope1)) {
                                                      final OptimizeProposition proposition1 = propsMap.get(decisionScope1)
                                                      // read proposition1 offers and display them
                                                }
                                                if (propositionsMap.contains(decisionScope2)) {
                                                      final OptimizeProposition proposition2 = propsMap.get(decisionScope2)
                                                      // read proposition2 offers and display them
                                                }
                                              }
                                        }
                                      });
                                }
                            });
```

>[!ENDTABS]

+++

+++ iOS example

>[!BEGINTABS]

>[!TAB Optimize SDK] 

```Swift

// Mboxes for Target activities
let decisionScope1 = DecisionScope(name: "myTargetMbox1")
let decisionScope2 = DecisionScope(name: "myTargetMbox2")
 
// Prefetch the Target mboxes
Optimize.updatePropositions(for: [decisionScope1, decisionScope2]
                            withXdm: ["xdmKey": "xdmValue"]
                            andData: ["dataKey": "dataValue"]) { data, error in
            if let error = error as? AEPOptimizeError {
                // handle error
                return
            }
            // Retrieve cached propositions if prefetch succeeds
            Optimize.getPropositions(for: [decisionScope1, decisionScope2]) { propositionsDict, error in
                if let error = error {
                    // handle error
                    return
                }
 
                if let propositionsDict = propositionsDict {
                    // get the propositions for the given decision scopes
 
                    if let proposition1 = propositionsDict[decisionScope1] {
                        // read proposition1 offers and display them
                    }
 
                    if let proposition2 = propositionsDict[decisionScope2] {
                        // read proposition2 offers and display them
                    }
                }
            }
        }

```

>[!ENDTABS]

+++



Next, learn how to [pass Target parameters using the Decisioning extension](send-parameters.md).

>[!NOTE]
>
>We are committed to helping you be successful with your mobile Target migration from the Target extension to the Decisioning extension. If you run into obstacles with your migration or feel like there is critical information missing in this guide, please let us know by posting in [this Community discussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463).
