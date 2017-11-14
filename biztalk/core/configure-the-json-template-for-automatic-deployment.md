---
redirect_url: /biztalk/core/feature-pack-add-application-project/
redirect_document_id: True
ROBOTS: NOINDEX
title: "Configurer le modèle JSON pour le déploiement automatique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 0b7755a6-5a5a-4a6b-8f99-ac12a5fbf3d4
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 10d85b625d759af675ecc1a38d540da8a304ba43
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configure-the-json-template-for-automatic-deployment"></a>Configurer le modèle JSON pour le déploiement automatique


Lorsque vous générez vos applications à l’aide de Visual Studio Team Services, un nouveau fichier de projet BizTalk est créée – (.btaproj). Ce projet conserve toutes les applications BizTalk que vous créez à l’aide de VSTS. 

Votre projet inclut le `BizTalkServerInventory.json` fichier. Dans ce fichier, ajouter vos assemblys BizTalk, ajoutez les fichiers de liaison pour votre application BizTalk et définir une séquence de déploiement. 

Cette rubrique montre comment mettre à jour le fichier json. 

## <a name="add-assemblies-binding-files-and-deployment-sequence"></a>Ajouter des assemblys, fichiers de liaison et la séquence de déploiement

1. Ouvrez le `BizTalkServerInventory.json` de fichiers dans votre **Application BizTalk Server** projet (.btaproj).

2. Le modèle inclut les sections suivantes : 

    | | |
    |---|---|
    |BizTalkAssemblies | Les assemblys utilisés dans vos applications |
    |BindingFiles | Les fichiers de liaison que vous référencez|
    | DeploymentSequence | La séquence des éléments à installer|
    
    Exemple de modèle : 
    
    ![Image de modèle FP1 Json 1](../core/media/fp1-json-template-image-1.png)

    > [!IMPORTANT]
    > Selon la complexité de votre solution, les éléments que vous souhaitez dans la build doivent être référencées dans ce fichier de modèle JSON.

3. Dans `BizTalkAssemblies`, ajoutez les assemblys utilisés par vos applications BizTalk : 

    ```
    "BizTalkAssemblies": [
        {
            "Name": "AssemblyName"
            "Path": "PathToAssembly
        }
    ]
    ```

4. Dans `BindingsFiles`, ajoutez les fichiers de liaison pour vos applications BizTalk : 

    ```
    "BindingsFiles": [
        {
            "Name": "Binding File Name"
            "Path": "PathToBindingFile
        }
    ]
    ```

5. Dans `DeploymentSequence`, ajoutez les noms d’application dans l’ordre que vous souhaitez les déployé et installé sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]: 

    ```
    "DeploymentSequence": [
        {
            "NameOfFirst", "NameOfSecond", "NameOfThird"
        }
    ]
    ```
    
6. **Enregistrer** vos modifications. 

Une fois terminé, la tâche de déploiement de Service Visual Studio Team honore les fichiers requis et la séquence d’installation. 

## <a name="next-step"></a>Étape suivante
[Configurer les variables et jetons](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md) dans votre fichier de liaison pour déployer la même application BizTalk à plusieurs [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]s.

 