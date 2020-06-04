
<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 0; ALERTS: 28.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>
<a href="#gdcalert2">alert2</a>
<a href="#gdcalert3">alert3</a>
<a href="#gdcalert4">alert4</a>
<a href="#gdcalert5">alert5</a>
<a href="#gdcalert6">alert6</a>
<a href="#gdcalert7">alert7</a>
<a href="#gdcalert8">alert8</a>
<a href="#gdcalert9">alert9</a>
<a href="#gdcalert10">alert10</a>
<a href="#gdcalert11">alert11</a>
<a href="#gdcalert12">alert12</a>
<a href="#gdcalert13">alert13</a>
<a href="#gdcalert14">alert14</a>
<a href="#gdcalert15">alert15</a>
<a href="#gdcalert16">alert16</a>
<a href="#gdcalert17">alert17</a>
<a href="#gdcalert18">alert18</a>
<a href="#gdcalert19">alert19</a>
<a href="#gdcalert20">alert20</a>
<a href="#gdcalert21">alert21</a>
<a href="#gdcalert22">alert22</a>
<a href="#gdcalert23">alert23</a>
<a href="#gdcalert24">alert24</a>
<a href="#gdcalert25">alert25</a>
<a href="#gdcalert26">alert26</a>
<a href="#gdcalert27">alert27</a>
<a href="#gdcalert28">alert28</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>



## Adobe Experience Platform: 


## Hands-On Technical Exercise: Identity Namespaces, Datasets, and DULE

V 1.0

Contents


[TOC]



## Overview

Now that you've created the XDM schema that's going to meet Luma's business goals, it's time to create identity namespaces, mark identity fields, create datasets, and establish proper data privacy controls via Data Usage Labeling and Enforcement (DULE) settings. 

Having a way for all of the data from the different sources to be tied together is one of the key value propositions of Platform and in this exercise, you'll see how to mark identity fields (in the XDM schema that you created in the previous exercise) and map them to identity namespaces. This will enable the creation of a unified profile that you'll see in the next set of exercises where the topic of Real-time Customer Profile will be introduced. 

Next, you'll learn how to create what Platform describes as datasets from the XDM Schema. An XDM schema defines what incoming data should look like while datasets are the acutal buckets of data that Platform uses to house the data. But of course, given today's privacy laws, governance needs to be enforced around how data in datasets can be used. This is where DULE comes into play.

 

Having correct DULE rules in place ensures that Personally Identifiable Information (PII) is only sent to places that Luma's customer privacy policy, as well as Adobe's, says that it can. Before Adobe Experience Platform, very few Adobe solutions such as Campaign and Marketo, were designed to store PII while other solutions like Audience Manager aren't allowed to have any PII data in it at all. There are still others like Analytics or Target where PII is strongly discouraged, but still able to be accepted so long as the client's legal team is okay with it. With Platform, one must now think holistically about the data captured and what types of data is more sensitive than others.  

Lastly, it's again important to call out that for this exercise you'll be using the Platform UI, but everything you're about to do in the UI can also be done via API call as well. 


## Create Identity Namespaces

Identity Namespaces are the mechanism used to inform Platform which identify fields from different XDM schemas house the same ids/data. In basic database terminology, it's how foreign keys are identified and connected between tables. We will need to use five namespaces to fully unify our schemas. Three of them will be default namespaces already in Platform while the remaining two we will be created this section.

Recall from the XDM building exercises that there were five fields that we put we created custom identity mixins for, namely:



*   CRM ID
*   Declared ID
*   Email ID
*   Phone Number
*   Loyalty ID

CRM ID, Declared ID, and Loyalty ID will need to have identity namespaces created for them. Phone Number and Email ID already have Adobe-owned namespaces that we'll simply reference. 



1. Log into https://platform.adobe.com with your adobe ID and ensure that you are in your assigned Experience Cloud org and in the sandbox you've created.
2. Click on **Identities** in the left rail

    

<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image001.png "image_tooltip")







3. We'll start by creating the CRM ID schema. Click on **Create identity namespace** in the upper right corner:

    

<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image002.png "image_tooltip")


4. In the **Create identity namespace** overlay, give it a display name of **CRM ID** and a symbol of **CRMID**. Also set the **Type** to **Cross-Device.** A description is optional, but is usually a good idea:

    **	**

<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image003.png "image_tooltip")
**.**

5. Click **Create**. When you’re redirected to the **Identity Namspace** page, click the **Browse** tab to see your newly created identity namespace:

    

<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image004.png "image_tooltip")



    **Note: **The owner is listed as Custom instead of Standard** **because it was custom created.

6. Create two more Identity namespaces with the following parameters:

<table>
  <tr>
   <td>
<strong>Display Name</strong>
   </td>
   <td><strong>Identity Symbol</strong>
   </td>
   <td><strong>Type</strong>
   </td>
  </tr>
  <tr>
   <td>Loyalty ID
   </td>
   <td>LoyaltyId
   </td>
   <td>Cross-Device
   </td>
  </tr>
  <tr>
   <td>Declared ID
   </td>
   <td>DeclaredId
   </td>
   <td>Cross-Device
   </td>
  </tr>
</table>



    Add a description for each field if you'd like. When finished, your Identity Namespaces should look like this:


    

<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image005.png "image_tooltip")




7. Scrolling down the list of standard identity namespaces, you should see the standard ones for phone and email that you'll use in a moment:

    

<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image6.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image006.png "image_tooltip")



    **Note:** You'll also see an ECID identity namespace. That will come into play later when you deploy the AEP Web SDK to the site. If you have an Audience Manager background, you'll also notice several familiar names in this list. One can think of identity namespaces like AAM data sources that were only used for id reconciliation with client or 3<sup>rd</sup> party data. 



## Update Schemas with Identity Namespacing Mapping

Now that you've created the appropriate Identity Namespaces, you're ready to map those namespaces to the XDM Schemas you created earlier. 



1. If necessary, log into platform.adobe.com and ensure you are in your assigned WWFO vLab### organization.
2. Click on **Schemas** in the left rail to view the 4 schemas you created.
3. Click into the **CRM Schema. **Next, expand the **wwofvlab### > Identification **nodes and select the **crmid** field. The right pane should show you the properties for this field:

    

<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image7.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image007.png "image_tooltip")


4. Scroll down in the right-hand pane and check the **Identity** checkbox:

    

<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image8.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image008.png "image_tooltip")


5. In the newly visible **Identity namespace** dropdown, you'll see all of the Identity Namespaces from the previous section, including the custom ones you created. As you may have probably guessed by now, you want to select the **CRM ID** identity namespace:

    

<p id="gdcalert9" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image9.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert10">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image009.png "image_tooltip")


6. This Identity is also going to be the **Primary Identity **for this schema, so you'll want to check the **Primary Identity** checkbox as well:

    

<p id="gdcalert10" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image10.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert11">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image010.png "image_tooltip")


7. Click **Apply** when done and you'll see the schema update with a thumbprint icon next to the crmid field as well as the mixin name update with which field has an identity:

    

<p id="gdcalert11" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image11.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert12">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image011.png "image_tooltip")


8. Click on the **declaredId** field, enable the **Identity** field, and select the **Declared ID** identity name space. Since you can only have one primary identity per schema, this identity is going to be called a secondary identity. As such, you will NOT check the Primary Identity field:

    

<p id="gdcalert12" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image12.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert13">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image012.png "image_tooltip")



    **Note: **The term 'secondary identity' is not an official term used by Adobe (you won't see it in the documentation anywhere). It's a term coined by those who have worked with customers to deploy Platform to help communicate and distinguish this identity to non-primary identity.

9. Click **Apply**. As with the previous identity, you'll see the declaredId field inherit the thumbnail icon and the additional identity appear in the mixin panel:

    

<p id="gdcalert13" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image13.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert14">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image013.png "image_tooltip")


10. Map the remaining two identity fields, **emailId and phoneNbr** to the **Email** and **Phone** identity namespaces as secondary identifiers. When finished, your CRM Schema should look like this:

    

<p id="gdcalert14" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image14.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert15">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image014.png "image_tooltip")


11. Save the **CRM Schema**. Then, return to the schemas homepage (click on **Schemas** in the left rail)
12. Click to expand **Offline Purchase** **Schema** and mark the only identity field there, **loyaltyId**, as the primary identity mapped to the custom **Loyalty ID** namespace. When finished, your schema should look like this:

    

<p id="gdcalert15" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image15.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert16">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image015.png "image_tooltip")


13. Save the **Offline Purchase** **Schema** then return to the schemas homepage.
14. Click to expand **Loyalty Schema**. Set the **loyaltyId** field as the **Primary Identifier** mapped to the **Loyalty ID** identity namespace.
15. Like the CRM Schema, set the **crmId, declaredId, emailId, **and **phoneNbr** field as a secondary identities mapped to their appropriate identity namespaces. Once finished, your **Loyalty Schema** should look like this:

     

<p id="gdcalert16" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image16.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert17">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image016.png "image_tooltip")



    **Note:** Even though the loyaltyId and cmrid fields appear in the same node, these two fields were created in different mixins (both custom mixins).

16. Save your schema and you're ready to move on to the next section.

    **Note**: You may be wondering why no identities were mapped in the fourth schema related to site data collection. Syncing data collected from the site with an identity map is done in the JavaScript itself. You'll get an opportunity to do that in a later exercise.



## Create Datasets and Apply DULE Settings

With the schemas built and identity fields marked and mapped to identity namespaces, we can now move to creating datasets, that will hold the actual data, from those schemas. However, we must also make sure that the data onboarded into these datasets has the proper data governance. With the advent of new privacy laws in the last few years, Adobe has decided to live by the mantra "Privacy by design". The Data Usage and Label Enforcement (DULE) settings you will apply when creating these datasets is the Platform's realization of that mantra and will help our clients, and Adobe, treat end user's data with the proper privacy. 



1. If necessary, log into platform.adobe.com and ensure you are in your assigned WWFO vLab### organization and sandbox you created earlier
2. Click on **Datasets** in the left rail and you'll be taken to the Datasets homepage. Click **Create dataset** in the upper right corner:

    

<p id="gdcalert17" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image17.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert18">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image017.png "image_tooltip")


3. On the Create dataset page, you'll see two options, one to create a dataset from a schema and another to create a dataset from a CSV file. Click the **Create dataset from schema** option.
4. We'll start with the CRM dataset. Select the **CRM Schema** option and click **Next:**

    

<p id="gdcalert18" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image18.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert19">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image018.png "image_tooltip")
 

5. Name the dataset **CRM Data** then click **Finish.** 
6. You should be taken to your newly created dataset page. Here we can do things like upload data (which you will do in a later exercise), view logs of previously uploaded data, and so forth. For right now, we need to apply the DULE settings needed for this dataset. Click the **Data governance **tab:

    

<p id="gdcalert19" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image19.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert20">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image019.png "image_tooltip")


7. Since this is CRM data, it will contain a lot of PII. As such, it'll need the most restrictive DULE settings. Click the **pencil icon** in the upper right to apply DULE settings for the entire dataset:

    

<p id="gdcalert20" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image20.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert21">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image020.png "image_tooltip")



    **Note: **That pencil icon doesn't resize with the rest of the window, so you may need to scroll horizontally or resize your window to find that icon.

8. On the resulting DULE screen, you'll see three groups of governance labels: Identity, Sensitive, and Contract. In the **Identity Labels **section (should be already expanded), check the **I2** option because a lot of this data can identity an individual rather than a device if used in conjunction with other data (more on this in a few steps):

    

<p id="gdcalert21" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image21.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert22">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image021.png "image_tooltip")


9. Expand the **Contract Labels** area and check the **C2** and **C5** options because most PII can't be sold to 3<sup>rd</sup> parties or be used for cross-internet advertising:

    

<p id="gdcalert22" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image22.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert23">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image022.png "image_tooltip")


10. Click **Save Changes **to save and close the overlay. You should then see the DULE labels appear next to all of the fields in the dataset:

    

<p id="gdcalert23" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image23.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert24">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image023.png "image_tooltip")


11. Scroll through the list of CRM fields in this dataset. Notice that there are some fields that will need a higher restriction. Check the **firstName, fullName, **and** lastName **fields then click the **Edit Governance Labels** to change the DULE settings for just these fields:

    

<p id="gdcalert24" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image24.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert25">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image024.png "image_tooltip")


12. Since these fields can absolutely be used to identity someone, they will need the I1 setting since the l2 settings aren't restrictive enough. Check the **I1** box then click **Save Changes**. You'll see that these new fields now show the higher level of restriction:

    

<p id="gdcalert25" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image25.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert26">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image025.png "image_tooltip")



    **Note: **If you scroll through, you'll notice that there are a LOT of fields. If you looked through the governance settings, you'll see a lot of DULE options as well! What you've done is just a small sampling of what could be done for proper data governance. Ultimately, it isn't Adobe's job to determine what DULE settings should be applied to what fields. There are some common ones that make sense that we walked you through here, but ultimately, it's up to the client's legal team to determine what data they capture needs to have what DULE settings applied to it. 


    The point of this exercise was to show you that DULE could be applied on both the dataset and individual field level. However, it's important to note that individual fields can only be more restrictive than the rules for the entire data set. We can't, for example, make the entire dataset I1 and then make something like birth year I2. As such, when marking an entire dataset, you'll want to apply the lowest level settings to the entire data set and then add more restrictive settings to individual fields as needed. 

13. With your DULE settings enabled, you're ready to create datasets for the rest of the schemas. Click on **Datasets** either in the left rail or in the top bread crumb trail (there is no save button to further save the DULE settings)
14. Using what you just learned create a new Dataset for the **Loyalty** Schema name **Loyalty Data** and because the data is not PII, you only need to apply an I2 DULE setting to the **crmid, emailId, **and** phoneNbr** fields. When finished, your new DULE settings should look like this:

    

<p id="gdcalert26" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image26.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert27">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image026.png "image_tooltip")


15. Create another dataset for the **Offline Purchase** schema called **Offline Purchase Data**. This data has no PII, but arguments could be made that the loyalty id could, through the loyalty schema, be tied to crm data. This is where the gray areas come into play because Platform does have the ability to merge this data with crm data. Therefore, should it have an I1 or I2 setting? Or no DULE settings at all? It'll depend on the client's legal team, but for our purposes, we won't need to add DULE setting. When finished, navigate back to the datasets homepage where you should see 3 datasets:

    

<p id="gdcalert27" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image27.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert28">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image027.png "image_tooltip")


16. Lastly, create one more dataset for the **Luma Website Schema** called **Luma Website Data**. Since this is website data and Luma had a consent management system, any customer that agrees to use the website also agrees to let Adobe collect data and use it for marketing purposes only. As such, there is also no need for DULE settings for our purposes. However, client legal teams could call out that if someone authenticates, then there is the ability to tie anonymous data to PII via Platform. Again, this is a gray area that would be up to the client's legal team to decide what DULE settings should be enforced. But for now, you just need to verify that that you now have 4 datasets:

    

<p id="gdcalert28" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image28.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert29">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](assets/image028.png "image_tooltip")



    Once you have all 4 datasets, you've completed this exercise. 


**Original Exercise Creators:**

Praveen Sharma and David Woolsey

**Exercise Contributors**:

Shruti Jagtap

**Change Log**


<table>
  <tr>
   <td>Ver.
   </td>
   <td>Issue Reporter
   </td>
   <td>Changes
   </td>
   <td>Date
   </td>
  </tr>
  <tr>
   <td>1.0
   </td>
   <td>
   </td>
   <td>Original Launch
   </td>
   <td>6/1/2020
   </td>
  </tr>
</table>

