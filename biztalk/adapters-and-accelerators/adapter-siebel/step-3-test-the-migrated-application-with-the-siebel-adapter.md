---
title: "Étape 3 : Tester l’Application migrée avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 651ee1b2-52da-497a-84a5-67f1436cc3e6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d72799af5221319db2f5f3243e09d984e13399c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-test-the-migrated-application-with-the-siebel-adapter"></a>Étape 3 : Tester l’Application migrée avec l’adaptateur Siebel
![Étape 3 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous allez tester l’application migrée en effectuant une opération d’insertion sur le composant de gestion de compte. Pour ce faire, vous supprimez un message de demande qui est conforme au schéma généré à l’aide de l’adaptateur Siebel vPrev.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Configurer l’application BizTalk en mappant les ports logiques de l’orchestration BizTalk aux ports physiques dans la console Administration de BizTalk Server.  
  
-   Configurer l’application BizTalk à utiliser le port d’envoi WCF-Custom pour la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
### <a name="to-test-the-migrated-application"></a>Pour tester l’application migrée  
  
1.  Dans le dossier Siebel_BussComp_Migration, copiez le message de demande AccountInsert.xml. Ce message de demande est conforme au schéma généré par l’adaptateur Siebel vPrev. À l’aide du mappage sortant, WCF-Custom envoyer convertit de port pour le rendre conforme au schéma pour la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] et l’envoie au système Siebel.  
  
    ```  
    <Insert xmlns="http://schemas.microsoft.com/[Siebel://Business Objects/Account/Account]">  
      <AccountInsertRecordSet>  
        <AccountInsertRecord xmlns="http://schemas.microsoft.com/Business_Objects">  
          <Currency_Code>USD</Currency_Code>  
          <Customer_Account_Group>Sold-To-Party</Customer_Account_Group>  
          <Location>Location_1</Location>  
          <Main_Phone_Number>012345678</Main_Phone_Number>  
          <Name>John_Smith</Name>  
          <Party_Name>Party_Name_1</Party_Name>  
          <Primary_Address_Id></Primary_Address_Id>  
        </AccountInsertRecord>  
      </AccountInsertRecordSet>  
    </Insert>  
    ```  
  
2.  Emplacement de réception de coller le message de demande dans le dossier mappé au fichier.  
  
3.  L’orchestration consomme le message de demande et l’envoie au système Siebel. La réponse à partir du système Siebel est reçue dans le schéma qui est conforme avec le schéma de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. À l’aide du mappage entrant, WCF-Custom envoyer port convertit le schéma pour l’adaptateur Siebel vPrev. La réponse à partir du système Siebel est enregistrée à l’autre emplacement de fichier définie dans le cadre de l’orchestration. La réponse pour le précédent message de demande est la suivante :  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ns0:InsertResponse xmlns:ns0="http://schemas.microsoft.com/[Siebel://Business Objects/Account/Account]" xmlns:exposed="http://schemas.microsoft.com" xmlns:Business_Objects="http://schemas.microsoft.com/Business_Objects">  
      <ns0:RowIDList>  
        <exposed:String>1-8EWWZ</exposed:String>  
      </ns0:RowIDList>  
    </ns0:InsertResponse>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 2 : Migration des projets BizTalk dans Siebel](../../adapters-and-accelerators/adapter-siebel/tutorial-2-migrating-biztalk-projects-in-siebel.md)