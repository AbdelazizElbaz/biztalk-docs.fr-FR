---
title: "Étape 3 : Tester l’application migrée à l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 495efc4f-9d9e-450f-a03a-628bb54e658f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30b5871aee85316b9885bd1ec22f4118c83743d1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-test-the-migrated-application-to-oracle-database-adapter"></a>Étape 3 : Tester l’application migrée à l’adaptateur de base de données Oracle
![Étape 3 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous allez tester l’application migrée en effectuant une opération d’insertion sur la SCOTT. Table CUSTOMER. Pour ce faire, vous supprimez un message de demande qui est conforme au schéma généré à l’aide de l’adaptateur de base de données Oracle vPrev.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Configurer l’application BizTalk en mappant les ports logiques de l’orchestration BizTalk aux ports physiques dans la console Administration de BizTalk Server.  
  
-   Configurer l’application BizTalk à utiliser le port d’envoi WCF-Custom pour la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
### <a name="to-test-the-migrated-application"></a>Pour tester l’application migrée  
  
1.  Dans le dossier Oracle_Migration, copiez le message de demande OracleInsert.xml. Ce message de demande est conforme au schéma généré par l’adaptateur de base de données Oracle vPrev. À l’aide du mappage sortant, WCF-Custom envoyer convertit de port pour le rendre conforme au schéma pour la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] et l’envoie à la base de données Oracle.  
  
    ```  
    <ns0:Insert xmlns:ns0="http://schemas.microsoft.com/[OracleDb://ADAPTER/SCOTT/Tables/CUSTOMER]">  
      <ns0:Rows>  
        <ns0:InsertRecord>  
          <ns0:NAME>Customer_1</ns0:NAME>  
          <ns0:STREET>Street_1</ns0:STREET>  
          <ns0:CITY>City_1</ns0:CITY>  
        </ns0:InsertRecord>  
        <ns0:InsertRecord>  
          <ns0:NAME>Customer_2</ns0:NAME>  
          <ns0:STREET>Street_2</ns0:STREET>  
          <ns0:CITY>City_2</ns0:CITY>  
        </ns0:InsertRecord>  
      </ns0:Rows>  
    </ns0:Insert>  
    ```  
  
2.  Emplacement de réception de coller le message de demande dans le dossier mappé au fichier.  
  
3.  L’orchestration consomme le message de demande et l’envoie à la base de données Oracle. Réception de la réponse à partir de la base de données Oracle dans le schéma qui est conforme avec le schéma de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. À l’aide du mappage entrant, WCF-Custom envoyer port convertit le schéma pour l’adaptateur de base de données Oracle vPrev. La réponse à partir de la base de données Oracle est enregistrée à l’autre emplacement de fichier définie dans le cadre de l’orchestration. La réponse pour le précédent message de demande est la suivante :  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ns0:InsertResponse xmlns:ns0="http://schemas.microsoft.com/[OracleDb://ADAPTER/SCOTT/Tables/CUSTOMER]"></ns0:InsertResponse>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Migration des projets BizTalk](https://msdn.microsoft.com/library/dd788186(v=bts.80).aspx)