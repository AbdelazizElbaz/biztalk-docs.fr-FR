---
title: "Étape 3 : Tester le Application6 migrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (RFC)
- migration
ms.assetid: 1b1ee59c-a5a3-442d-af2c-0fc4817f3063
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ebc175053b7afa1f3c360623b0230809db17bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-test-the-migrated-application"></a>Étape 3 : Tester l’Application migrée
![Étape 3 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous allez tester l’application migrée en appelant la RFC SD_RFC_CUSTOMER_GET. Pour ce faire, vous supprimez un message de demande qui est conforme au schéma généré à l’aide de l’adaptateur SAP vPrev.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Configurer l’application BizTalk en mappant les ports logiques de l’orchestration BizTalk aux ports physiques dans la console Administration de BizTalk Server.  
  
-   Configurer l’application BizTalk à utiliser le port d’envoi WCF-Custom pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### <a name="to-test-the-migrated-application"></a>Pour tester l’application migrée  
  
1.  Dans le dossier SAP_RFC_Migration, copiez le message de demande Input.xml. Ce message de demande est conforme au schéma généré par l’adaptateur SAP vPrev. À l’aide du mappage sortant, WCF-Custom envoyer convertit de port pour le rendre conforme au schéma pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et l’envoie au système SAP.  
  
    ```  
    <ns0:SD_RFC_CUSTOMER_GET_Request xmlns:ns0="http://schemas.microsoft.com/BizTalk/2003">  
      <KUNNR>0000001390</KUNNR>  
      <NAME1/>  
      <CUSTOMER_T/>  
    </ns0:SD_RFC_CUSTOMER_GET_Request>  
    ```  
  
2.  Emplacement de réception de coller le message de demande dans le dossier qui est mappé au fichier.  
  
3.  L’orchestration consomme le message de demande et l’envoie au système SAP. Réception de la réponse du système SAP dans le schéma qui est conforme avec le schéma de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. À l’aide du mappage entrant, WCF-Custom envoyer port convertit le schéma pour l’adaptateur SAP vPrev. La réponse du système SAP est enregistrée à l’autre emplacement de fichier définie dans le cadre de l’orchestration. La réponse pour le précédent message de demande est :  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <ns0:SD_RFC_CUSTOMER_GET_Response xmlns:ns0="http://schemas.microsoft.com/BizTalk/2003">  
      <CUSTOMER_T>  
        <KUNNR>0000001390</KUNNR>   
        <ANRED>Firma</ANRED>   
        <NAME1>Contoso, Ltd.</NAME1>   
        <PFACH />   
        <STRAS>Strasse 4567</STRAS>   
        <PSTLZ>50000</PSTLZ>   
        <ORT01>Aachen</ORT01>   
        <TELF1>0123-45678</TELF1>   
        <TELFX>0123-56789</TELFX>   
      </CUSTOMER_T>  
    </ns0:SD_RFC_CUSTOMER_GET_Response>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 2 : Migration d’un projet BizTalk RFC SAP](../../adapters-and-accelerators/adapter-sap/tutorial-2-migrating-an-sap-rfc-biztalk-project.md)