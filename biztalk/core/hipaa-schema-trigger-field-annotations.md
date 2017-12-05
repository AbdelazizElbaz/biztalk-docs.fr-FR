---
title: "Annotations des champs déclencheurs HIPAA schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1389284-a2ec-44e7-a2f1-8d26f83fd31d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8c50db43b14899439877fde8ce0ee476feb5095
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="hipaa-schema-trigger-field-annotations"></a>Annotations des champs déclencheurs de schéma HIPAA
Les segments EDI contiennent souvent des valeurs du qualificateur qui modifient la signification d'un segment. Par exemple, un segment N1 peut contenir un élément de qualification « BT » signifiant « Nom de facturation (bill-to) » ou « ST » pour « Nom de livraison (ship-to) ». Normalement, il reste à la logique métier pour déterminer comment interpréter ces champs et le désassembleur fait correspondre toutes les instances du segment N1 avec le même nom de l’enregistrement XML ; Toutefois, les schémas HIPAA inclus dans BizTalk Server contiennent des annotations permettant au désassembleur EDI créer des enregistrements XML uniques en fonction de la présence d’un élément de qualification.  
  
 **Implémentation du champ déclencheur**  
  
 Les champs déclencheurs sont implémentés en tant que paire d'attributs XML décrivant l'élément de segment et la valeur de déclenchement qui provoque la création de cet enregistrement. Le tableau suivant présente ces attributs :  
  
|Attribut|Fonction|  
|---------------|-------------|  
|trigger_field|Champ du segment dans lequel la valeur de déclenchement est recherchée.|  
|trigger_value|La ou les valeurs de déclenchement.<br /><br /> Ce champ peut contenir une seule valeur ou une liste de valeurs délimitées par des espaces.|  
  
 Le tableau suivant illustre l'annotation de déclenchement telle qu'affichée dans le schéma HIPAA, le segment EDI provoquant l'activation du déclencheur ainsi que les données XML résultant du traitement du segment.  
  
|Annotation de déclenchement du schéma|Segment N1 correspondant|Données XML résultantes|  
|-------------------------------|-------------------------|------------------------|  
|`<xs:element name="TS835W1_1000A_Loop">  <xs:annotation>   <xs:appinfo>    <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayerIdentification_TS835W1_1000A/N101__EntityIdentifierCode"     trigger_value="PR" notes="Payer Identification" />    </xs:appinfo>  </xs:annotation>`|N1 * PR\*Contoso\*XV\*0000000 ~|`<ns0:TS835W1_1000A_Loop>  <N1_PayerIdentification_TS835W1_1000A>   <N101__EntityIdentifierCode>PR</N101__EntityIdentifierCode>    <N102__PayerName>Contoso</N102__PayerName>    <N103__IdentificationCodeQualifier>XV</N103__IdentificationCodeQualifier>    <N104__PayerIdentifier>0000000</N104__PayerIdentifier>   </N1_PayerIdentification_TS835W1_1000A>`|  
|`<xs:element name="TS835W1_1000B_Loop">   <xs:annotation>    <xs:appinfo>     <b:recordInfo structure="delimited" delimiter_type="inherit_record"     field_order="infix" count_ignore="yes" child_delimiter="default"     trigger_field="N1_PayeeIdentification_TS835W1_1000B/N101__EntityIdentifierCode"     trigger_value="PE" notes="Payee Identification" />    </xs:appinfo>   </xs:annotation>`|N1 * PE\*Fabrikam\*FI\*9999999 ~|`<TS835W1_1000B_Loop>   <N1_PayeeIdentification_TS835W1_1000B>    <N101__EntityIdentifierCode>PE</N101__EntityIdentifierCode>    <N102__PayeeName>Fabrikam</N102__PayeeName>    <N103__IdentificationCodeQualifier>FI</N103__IdentificationCodeQualifier>    <N104__PayeeIdentificationCode>9999999</N104__PayeeIdentificationCode>   </N1_PayeeIdentification_TS835W1_1000B>`|  
  
 **Traitement du désassembleur EDI des champs déclencheurs**  
  
 Lors de la réception d’une transaction HIPAA définie, si le désassembleur EDI rencontre un segment qui contient un champ déclencheur, il utilise les informations de déclencheur pour générer un enregistrement XML spécifique à la combinaison segment / déclencheur. Par exemple, dans les données EDI suivantes, deux segments N1 possèdent des valeurs distinctes pour N101, PR et PE.  
  
```  
  
N1*PR*Contoso*XV*0000000~  
N3*N301__PayerAddressLine~  
N4*N401__PayerCityName*N4*N403__PayerPost**N4*N406~  
……  
N1*PE*Fabrikam*FI*9999999~  
N3*N301__PayeeAddressLine~  
N4*N401__PayeeCityName*N4*N403__PayeePost**N4*N406~  
  
```  
  
 Lors du traitement par le désassembleur EDI, les annotations du champ déclencheur présentes dans le schéma entraîne deux enregistrements XML distincts en fonction de la valeur de N101, < N1_PayerIdentification_TS835W1_1000A > et < N1_PayeeIdentification_TS835W1_1000B >, correspondant à N1 * PR et N1\*PE.  
  
 Lors de l'envoi, le Désassembleur EDI abandonne le suffixe situé après le caractère « _ » pour les champs contenant une annotation de déclenchement. Par exemple, <N1_PayerIdentification_TS835W1_1000A> et <N1_PayeeIdentification_TS835W1_1000B> sont transformés tous les deux en N1.  
  
 **Champs déclencheurs et Segments par défaut**  
  
 Le tableau suivant contient des informations sur les segments de valeur par défaut et les champs de déclencheur utilisés dans les documents HIPAA inclus en tant que partie de BizTalk Server :  
  
> [!NOTE]
>  Les valeurs de déclencheur individuelles utilisées avec les champs déclencheurs peuvent varier selon les schémas.  
  
|Segment avec déclencheur|Champ déclencheur|  
|--------------------------|-------------------|  
|AMT|AMT01|  
|CRC|CRC01|  
|DTM|DTM01|  
|DTP|DTP01|  
|ENT|ENT02|  
|HI|HI01:01|  
|N1|N101|  
|NM1|NM01|  
|NTE|NTE01|  
|REF|REF01|  
|RMR|RMR01|