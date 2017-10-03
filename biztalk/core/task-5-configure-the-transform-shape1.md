---
title: "Tâche 5 : Configurer la transformation Shape1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93a73fd2-0f34-4681-8aed-7d54d69c86d3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e76313ca87ad3138da83480b46a38a802d89ff15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-5-configure-the-transform-shape"></a>Tâche 5 : Configurer la forme Transformer
Les procédures suivantes permettent de configurer la forme Transformer.  
  
### <a name="to-configure-the-transform-shape"></a>Pour configurer la forme Transformer  
  
1.  Faites glisser une forme Construire un message après ReceiveBeginDocResponse.  
  
    -   **Messages construits :** EditLineMsg  
  
    -   **Nom :** ConstructEditLineMessageWithData  
  
     Avec le bouton droit au milieu, sélectionnez **insérer une forme**, puis sélectionnez **transformer**.  
  
     ![](../core/media/jde-insert-shape-transform.gif "JDE_insert_shape_transform")  
  
     À l'aide de la forme Transformer, mappez les données depuis les données que vous envoyez vers les données envoyées.  
  
     Vous devez envoyer un document (au lieu de BeginDoc) pour votre environnement de travail, avec toutes les valeurs possibles afin de construire tous les messages possibles (BeginDoc, EditLine et EndDoc). Toutefois, seules des données codées en dur sont utilisées dans cet exemple.  
  
2.  Double-cliquez sur **Transform_1** à ouvrir.  
  
    1.  Sélectionnez Source, cliquez dans la ligne Ajouter sous **nom de la Variable** et sélectionnez **BeginDocResponseMsg**.  
  
         ![](../core/media/jde-transform-source.gif "JDE_transform_source")  
  
    2.  Sélectionnez **Destination** et cliquez sur dans la ligne Ajouter sous **nom de la Variable**, sélectionnez **EditLineMsg**, puis cliquez sur **OK**.  
  
         ![](../core/media/jde-transform-destination.gif "JDE_transform_destination")  
  
3.  Dans l’Explorateur de solutions, double-cliquez sur **Transform_1.btm** pour ouvrir l’outil de mappage. Liez les quatre éléments suivants :  
  
    -   mnCMJobNo  
  
    -   szCMComputerID  
  
    -   mnProcessID  
  
    -   mnTransactionID  
  
     ![](../core/media/jde-example-transformmapping.gif "JDE_example_transformmapping")  
  
     Dans un souci de simplicité d'utilisation, cet exemple inclut des valeurs codées en dur. Cliquez sur l'élément dans le schéma de destination et définissez la valeur suivante.  
  
     ![](../core/media/jde-hardcoded-mapping-example.gif "JDE_hardcoded_mapping_example")  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ns0:F4211FSEditLine xmlns:ns0="http://schemas.microsoft.com/  
          [JDE://CSALES/B4200310]">  
       <ns0:cCMLineAction>A</ns0:cCMLineAction>  
       <ns0:cCMProcessEdits>1</ns0:cCMProcessEdits>  
       <ns0:cCMWriteToWFFlag>2</ns0:cCMWriteToWFFlag>  
       <ns0:szItemNo>210</ns0:szItemNo>  
       <ns0:mnQtyOrdered>1</ns0:mnQtyOrdered>  
       <ns0:cSalesTaxableYN>N</ns0:cSalesTaxableYN>  
       <ns0:szTransactionUOM>EA</ns0:szTransactionUOM>  
       <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
       <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
    </ns0:F4211FSEditLine>  
    ```  
  
4.  Faites glisser une forme Construire un message après ReceiveEditLine.  
  
    -   **Messages construits :** EndDocMsg  
  
    -   **Nom :** ConstructEndDocMessageWithData  
  
     Avec le bouton droit dans le milieu et sélectionnez **insérer une forme**, puis sélectionnez **transformer**.  
  
5.  Double-cliquez sur **Transform_2** à ouvrir.  
  
    1.  Sélectionnez **Source** et cliquez sur dans la ligne Ajouter sous **nom de la Variable** et sélectionnez **BeginDocResponseMsg**.  
  
    2.  Sélectionnez **Destination** et cliquez sur dans la ligne Ajouter sous **nom de la Variable**, sélectionnez **EndDocMsg**, puis cliquez sur **OK**.  
  
6.  Dans l’Explorateur de solutions, double-cliquez sur **Transform_2.btm** pour ouvrir l’outil de mappage. Liez les quatre éléments suivants :  
  
    -   mnCMJobNo  
  
    -   szCMComputerID  
  
    -   mnProcessID  
  
    -   mnTransactionID  
  
     Dans un souci de simplicité d'utilisation, cet exemple inclut des valeurs codées en dur. Cliquez sur l'élément dans le schéma de destination et définissez la valeur suivante.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ns0:F4211FSEndDoc xmlns:ns0="http://schemas.microsoft.com/  
        [JDE://CSALES/B4200310]">  
       <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
       <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
       <ns0:cCMUseWorkFiles>2</ns0:cCMUseWorkFiles>  
    </ns0:F4211FSEndDoc>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche 1 : Créer les Ports](../core/task-1-create-the-ports2.md)   
 [Tâche 2 : Créer les Messages](../core/task-2-create-the-messages1.md)   
 [Tâche 3 : Configurer l’envoi et réception des formes](../core/task-3-configure-the-send-and-receive-shapes1.md)   
 [Tâche 4 : Configurer la forme construire un Message](../core/task-4-configure-the-construct-message-shape2.md)