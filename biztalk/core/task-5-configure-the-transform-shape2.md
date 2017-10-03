---
title: "Tâche 5 : Configurer la transformation Shape2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e92874e-9021-4cf6-bab6-d4173308c469
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 596afdecc38f25ef92dbeb368197d9c71adaffc5
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
  
    1.  Avec le bouton droit au milieu, sélectionnez **insérer une forme**, puis sélectionnez **transformer**.  
  
         ![Insérer la forme transformer](../core/media/insert-shape-transform.gif "insert_shape_transform")  
  
    2.  À l'aide de la forme Transformer, mappez les données depuis les données que vous envoyez vers les données envoyées.  
  
     Vous devez envoyer un document (au lieu de BeginDoc) pour votre environnement de travail, avec toutes les valeurs possibles afin de construire tous les messages possibles (BeginDoc, EditLine et EndDoc). Toutefois, seules des données codées en dur sont utilisées dans cet exemple.  
  
2.  Double-cliquez sur Transform_1 pour l'ouvrir.  
  
    1.  Sélectionnez Source, cliquez dans la ligne Ajouter sous **nom de la Variable** et sélectionnez **BeginDocResponseMsg**.  
  
         ![Transformation Source](../core/media/transform-source.gif "transform_source")  
  
    2.  Sélectionnez **Destination** et cliquez sur dans la ligne Ajouter sous **nom de la Variable**, sélectionnez **EditLineMsg**, puis cliquez sur **OK**.  
  
         ![Transformer la Destination](../core/media/transform-destination.gif "transform_destination")  
  
3.  Dans l’Explorateur de solutions, double-cliquez sur **Transform_1.btm** pour ouvrir l’outil de mappage. Liez les quatre éléments suivants :  
  
    -   mnCMJobNo  
  
    -   szCMComputerID  
  
    -   mnProcessID  
  
    -   mnTransactionID  
  
     ![Exemple transformer mappage](../core/media/example-transformmapping.gif "example_transformmapping")  
  
     Dans un souci de simplicité d'utilisation, cet exemple inclut des valeurs codées en dur. Cliquez sur l'élément dans le schéma de destination et définissez la valeur suivante.  
  
     ![Mappage de codé dur](../core/media/hardcoded-mapping-example.gif "hardcoded_mapping_example")  
  
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
  
5.  Double-cliquez sur Transform_2 pour l'ouvrir.  
  
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
 [Tâche 1 : Créer les Ports](../core/task-1-create-the-ports1.md)   
 [Tâche 2 : Créer les Messages](../core/task-2-create-the-messages2.md)   
 [Tâche 3 : Configurer l’envoi et réception des formes](../core/task-3-configure-the-send-and-receive-shapes2.md)   
 [Tâche 4 : Configurer la forme construire un Message](../core/task-4-configure-the-construct-message-shape1.md)