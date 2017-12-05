---
title: "Appeler des méthodes de Service d’entreprise avec des objets d’intégration à l’aide de l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- integration objects
- how to, invoke business service methods with integration objects
- business service methods, invoking with integration objects
ms.assetid: ac0fa80a-3451-436e-8a1a-b6b5e93081e7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 132c269d347f67cbad3038bcbbb8e62d29112b6e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-business-service-methods-with-integration-objects-using-the-siebel-adapter"></a>Appeler des méthodes de Service d’entreprise avec des objets d’intégration à l’aide de l’adaptateur Siebel
Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] permet aux clients d’adaptateur appeler des méthodes de service d’entreprise qui fonctionnent avec les objets d’intégration. Ces services professionnels ont généralement IN, OUT, ou dans les paramètres de données de « hiérarchie » de type pour envoyer ou recevoir des données d’objet intégration.  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose ces types hiérarchiques sous forme de chaînes. Ces valeurs de chaîne sont essentiellement une chaîne XML est encapsulée dans une section CDATA XML. La chaîne XML est compatible avec le schéma XML de l’objet d’intégration que le client de l’adaptateur tente d’envoyer ou recevoir.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, SiebelAdapterIntegrationObjects, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples pour l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md).
  
## <a name="creating-an-orchestration-to-invoke-business-service-methods-with-integration-objects"></a>Création d’une Orchestration pour appeler des méthodes de Service d’entreprise avec des objets d’intégration  
 Création d’une orchestration pour appeler une méthode de service d’entreprise qui utilise des paramètres de l’objet d’intégration est similaire à l’orchestration à appeler n’importe quel autre service d’entreprise, comme décrit dans [appeler Business Service méthodes à l’aide de BizTalk Server et l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md).  
  
 La différence réside dans le message de demande que vous déposez pour l’orchestration. Cela s’explique par le texte suivant :  
  
-   Le schéma du message de requête est différent, car vous appelez un service d’entreprise différents.  
  
-   Le message de demande contient la chaîne XML de l’objet d’intégration. Ce code XML est encapsulé dans une section CDATA. Vous devez tout d’abord générer le schéma pour l’objet d’intégration et ensuite créer un document XML conforme au schéma. Ce document XML doit être passé au sein de la section CDATA du message de demande envoyée à l’adaptateur.  
  
 Une fois que vous avez généré le code XML qui est conforme au schéma d’objet intégration et inclus dans le message de demande, vous devez supprimer le message de demande à un emplacement de fichier, exactement comme vous le feriez pour n’importe quel autre orchestration. Recherchez le message de réponse dans l’autre emplacement de fichier.  
  
## <a name="request-and-response-messages-for-invoking-business-service-with-integration-objects"></a>Messages de demande et réponse pour l’appel de Service d’entreprise avec des objets d’intégration  
 Comme mentionné précédemment, la seule différence pour appeler un service d’entreprise qui utilise des paramètres de l’objet d’intégration est le message de demande envoyé à l’adaptateur. Cette section fournit des instructions sur la procédure à qu'effectuer pour créer le message de demande.  
  
 Pour mieux comprendre, prenons l’exemple un service d’entreprise Siebel 'EAI l’adaptateur Siebel'. Le service d’entreprise 'EAI l’adaptateur Siebel' fonctionne sur un objet d’intégration de Siebel, « Compte de l’exemple ». Vous devez effectuer les tâches suivantes pour créer le message de demande pour appeler une méthode exposée par le service d’entreprise 'EAI l’adaptateur Siebel' :  
  
-   **Générer le schéma pour le service d’entreprise EAI l’adaptateur Siebel**. Vous devez utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma. Une fois que vous générez le schéma, générer le code XML qui est conforme au schéma.  
  
-   **Générer le schéma pour l’objet d’intégration**. Utilisez les outils de Siebel pour générer le schéma d’un objet d’intégration. Dans l’interface Outils Siebel, sélectionnez l’objet d’intégration, par exemple, exemple de compte, puis cliquez sur **générer le schéma**. Lors de la génération du schéma, assurez-vous que :  
  
    -   Le **sélectionner un Service d’entreprise à partir de la liste** déroulante a la valeur « EAI XML XSD Generator ».  
  
    -   Le **sélectionnez un type d’enveloppe dans la liste** déroulante a la valeur « Enveloppe de Message Siebel ».  
  
     Pour plus d’informations, consultez la documentation de Siebel.  
  
-   **Créer un message XML conforme au schéma de l’objet d’intégration**. Un exemple de message XML généré pour l’objet d’intégration 'Exemple compte' ressemble à :  
  
    ```  
    <?xml version="1.0" encoding="UTF-16"?>  
    <SiebelMessage  MessageId="" IntObjectName="Sample Account" MessageType="Integration Object" IntObjectFormat="Siebel Hierarchical">  
      <ListOfSampleAccount>  
        <Account>  
          <CurrencyCode>USD</CurrencyCode>  
          <Location>Redmond</Location>  
          <Name>IntegrationObjectTest</Name>  
        </Account>  
      </ListOfSampleAccount>  
    </SiebelMessage>  
    ```  
  
-   **Passer ce message XML en tant que la valeur de l’élément CDATA dans le message de demande pour la méthode de service business**. Un exemple de message de demande qui contient le message XML au sein d’un élément CDATA ressemble à ceci. Cet exemple de demande est d’appeler la méthode d’insertion pour le service d’entreprise 'EAI l’adaptateur Siebel'.  
  
    ```  
    <Insert xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter/Operation">  
      <InsertRequestRecord />   
      <InsertInOutRecord>  
        <SiebelMessage xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">  
          <![CDATA[ <?xml version="1.0" encoding="UTF-16"?>  
            <SiebelMessage  MessageId="" IntObjectName="Sample Account" MessageType="Integration Object" IntObjectFormat="Siebel Hierarchical">  
              <ListOfSampleAccount>  
                <Account>  
                  <CurrencyCode>USD</CurrencyCode>  
                  <Location>Redmond</Location>  
                  <Name>IntegrationObjectTest</Name>  
                </Account>  
              </ListOfSampleAccount>  
            </SiebelMessage>  
          ]]>   
         </SiebelMessage>  
      </InsertInOutRecord>  
    </Insert>  
    ```  
  
     La réponse à partir de Siebel pour le message de demande ci-dessus ressemble à ceci :  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <InsertResponse xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter/Operation">  
      <InsertResult>  
        <ErrorCode xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">0x0</ErrorCode>   
        <ErrorContextIntComp xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <ErrorContextSearchSpec xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <ErrorSymbol xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <OMErrorCode xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <OMErrorSymbol xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter" />   
        <PrimaryRowId xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">1-6SPSJ</PrimaryRowId>   
      </InsertResult>  
      <InsertInOutRecord>  
        <SiebelMessage xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/EAI_x0020_Siebel_x0020_Adapter">  
          <![CDATA[ <?xml version="1.0" encoding="UTF-16"?>  
            <SiebelMessage  MessageId="" IntObjectName="Sample Account" MessageType="Integration Object" IntObjectFormat="Siebel Hierarchical">  
              <ListOfSampleAccount>  
                <Account>  
                  <CurrencyCode>USD</CurrencyCode>  
                  <Location>Redmond</Location>  
                  <Name>IntegrationObjectTest</Name>  
                </Account>  
              </ListOfSampleAccount>  
            </SiebelMessage>  
          ]]>   
         </SiebelMessage>  
      </InsertInOutRecord>  
    </InsertResponse>  
    ```  
  
 À l’aide des fonctionnalités de BizTalk, les clients de l’adaptateur peuvent également effectuer une validation supplémentaire de l’intégration IN et OUT paramètre de l’objet par rapport au schéma d’objet integration (obtenu à partir des outils de Siebel).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des Applications BizTalk à l’aide de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)    
[Développer vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)