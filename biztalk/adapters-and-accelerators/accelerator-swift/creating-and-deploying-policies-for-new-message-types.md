---
title: "Création et déploiement de stratégies pour les nouveaux Types de messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43343238-ec45-44ed-a230-9e234bd22d05
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b89972b2b84927fc16b14184338ca4920e984656
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-deploying-policies-for-new-message-types"></a>Création et déploiement de stratégies pour les nouveaux Types de Message
Pour créer et déployer des stratégies pour les nouveaux types de message :  
  
1.  Créer un dossier portant le nom du type de message à l’intérieur du dossier MX Messages. Par exemple, dans ce cas le nom du dossier serait setr.004.001.02.  
  
    ```csharp  
    (<xs:complexType name="Document">  
        <xs:sequence>  
            <xs:element name="setr.004.001.02" type="setr.004.001.02"/>  
        </xs:sequence>  
    </xs:complexType>)  
    ```  
  
2.  Placez le fichier de schéma (*.xsd), ainsi que le maître résultant / stratégie de validation du fichier pour ce type de message dans ce dossier.  
  
3.  Mettre à jour le MXMessageTypeKeywordList.xml (C:\Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tools) avec un nom de mot clé. Ce nom doit être les quatre premières lettres du nom du dossier de message. Par exemple :  
  
    ```csharp  
    (<Keyword name ="setr" />)  
    ```  
  
4.  Pour créer le maître spécifique, les stratégies de validation, effectuer une copie de la base, les fichiers de stratégie de validation existants de message et de le placer dans le nouveau dossier de message.  
  
5.  Modifiez toutes les références aux types de messages dans le master / stratégie de validation afin de refléter les nouveaux types de message.  
  
## <a name="message-naming-conventions"></a>Conventions d’affectation de noms de message  
 Suivre les conventions pour les noms de message :  
  
-   **En remplaçant le nom du message**: si le nouveau nom de message est swift.if.ia.setr.004.001.02 et l’ancien message dont les fichiers stratégie ont été utilisées est pacs.002.001.02, puis remplacez toutes les occurrences de pacs.002.001.02 avec SWIFT.If.IA.setr.004.001.02 dans les fichiers de stratégie.  
  
    > [!NOTE]
    >  Nom du message est le nom du fichier de schéma qui a été téléchargé et type de message est le nom du type de document dans le message.  
  
-   Conservez le nom des fichiers de stratégie dans le même que le schéma du message lui-même. Par exemple, swift.if.ia.setr.004.001.02.xsd aura suivant _Validation_Policy.xml _Master_Policy.xml et swift.if.ia.setr.004.001.02 du swift.if.ia.setr.004.001.02 stratégies.  
  
-   **Caractères spéciaux**: si le nom du message compte des caractères spéciaux, création d’un fichier de stratégie requiert une convention légèrement différente. Si le nom du message est, par exemple, swift.if.ia$setr.004.001.02, alors que vous devez modifier le nom du fichier de stratégie pour le nom du message avec les caractères spéciaux qui est remplacées par «. » Par exemple, si le nom du fichier de schéma de message est swift.if.ia$setr.004.001.02.xsd, la stratégie maître résultante serait swift.if.ia.setr.004.001.02_Master_Policy.xml.  
  
     Le fichier de stratégie principal doit également être modifiées pour refléter le nouveau nom dans les balises suivantes :  
  
    -   \<ensemble de règles name="swift.if.ia.setr.004.001.02_Master_Policy » >  
  
    -   < règle name="swift.if.ia.setr.004.001.02_Policy_List »