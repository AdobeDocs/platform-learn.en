$$BEGIN



DROP TABLE IF EXISTS t_ame_customer_profiles;



CREATE TABLE t_ame_customer_profilesAS

SELECT *

FROM (

SELECT LPAD(_b2wdigital.identities.cpf::text, 11, '0') AS cpf

,_b2wdigital.ame.b2w_employee AS b2w_employee

,_b2wdigital.ame.birth_date AS birth_date

,_b2wdigital.ame.dias_conta_ativa AS dias_conta_ativa

,_b2wdigital.ame.email AS email

,_b2wdigital.ame.endereco AS endereco

,_b2wdigital.ame.first_transac_created_at AS first_transac_created_at

,_b2wdigital.ame.first_transac_order_type AS first_transac_order_type

,_b2wdigital.ame.genero AS genero

,_b2wdigital.ame.last_transac_created_at AS last_transac_created_at

,_b2wdigital.ame.last_transac_order_type AS last_transac_order_type

,_b2wdigital.ame.merchant AS merchant

,_b2wdigital.ame.merchant_first_transac AS merchant_first_transac

,_b2wdigital.ame.merchant_last_transac AS merchant_last_transac

,_b2wdigital.ame.merchant_qtd AS merchant_qtd

,_b2wdigital.ame.merchant_since AS merchant_since

,_b2wdigital.ame.merchant_value AS mercahnt_value

,_b2wdigital.ame.nome AS nome

,_b2wdigital.ame.phone AS phone

,_b2wdigital.ame.state AS state

,_b2wdigital.ame.system AS system

,_b2wdigital.ame.total_qtd AS total_qtd

,_b2wdigital.ame.total_value AS total_value

,_b2wdigital.ame.updated_at AS updated_at

,_b2wdigital.ame.wallet_created_at AS wallet_created_at

,_b2wdigital.ame.wallet_id AS wallet_id

,ROW_NUMBER() OVER (PARTITION BY LPAD(_b2wdigital.identities.cpf::text, 11, '0') ORDER BY_b2wdigital.ame.updated_at DESC) AS row_num

FROM ame_profile_customer_dataset

WHERE _b2wdigital.identities.cpf IS NOT NULL

AND _b2wdigital.identities.cpf::bigint> 0

--AND _b2wdigital.identities.cpf = '32109140879' -- remove after testing

)

WHERE row_num = 1;



END$$;