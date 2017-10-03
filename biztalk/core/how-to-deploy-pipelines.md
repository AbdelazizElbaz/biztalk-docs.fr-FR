---
title: "Comment déployer des Pipelines | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IReceiveLocation interface
- IReceivePort interface
- deploying, pipelines
- pipelines, deploying
- pipelines, compiling
- SendPipelineData method
- pipelines, configuring
- pipelines, code sample
- ReceivePipelineData property
- Validate method
- ISendPort interface
ms.assetid: 7a56c753-a0d4-48ed-a61d-e454bc9cd507
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db6047752c45a2f72b615102e14a4e66839e3e81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-pipelines"></a>Déploiement des pipelines
Les pipelines sont compilés et déployés dans le cadre du processus de création et de déploiement de solutions. Le compilateur appelle le **Validate** méthode sur chaque composant, en autorisant les composants retourner des erreurs de compilation dans les informations configurées. Après sa création, le pipeline est déployé dans le même assembly que le reste de la solution dès que celle-ci est déployée.  
  
## <a name="per-instance-pipeline-configuration"></a>Configuration de pipeline par instance  
 La configuration de pipeline par instance est utilisée pour modifier les propriétés de composants de pipeline dans un pipeline déployé au niveau du port d'envoi ou de l'emplacement de réception. Elle est utile lorsque seules quelques propriétés de composant de pipeline doivent être modifiées par instance. Par exemple, si vous devez prendre en charge différents types de message dans plusieurs emplacements de réception et possédez un pipeline de réception XML personnalisé, la configuration de pipeline par instance vous permet de déployer le pipeline et de remplacer la configuration par défaut (notamment la spécification de différents noms d'enveloppe et de document). Ce mécanisme est pris en charge dans BizTalk Management Console et au niveau logiciel par l'intermédiaire du modèle objet de l'Explorateur.  
  
### <a name="per-instance-pipeline-configuration-using-biztalk-administration-console"></a>Configuration de pipeline par instance à l'aide de la console Administration de BizTalk  
 Vous pouvez effectuer la configuration de pipeline par instance à l'aide de BizTalk Management Console. Une fois votre pipeline personnalisé déployé, créez le nombre nécessaire d'emplacements de réception et de ports d'envoi. Ensuite, pour chaque emplacement de réception ou port d'envoi, remplacez les valeurs de propriété par défaut par l'intermédiaire de la boîte de dialogue Configurer le pipeline. Par exemple, pour spécifier un schéma de document différent, entrez un nom de schéma pour le **EnvelopeDocSpecNames** propriété.  
  
> [!WARNING]
>  Aucune validation des valeurs de configuration spécifiées dans l'emplacement de réception ou le port d'envoi sera effectuée. Si la configuration est incorrecte, les messages échoueront au moment de l'exécution lors de la transmission via le pipeline.  
  
### <a name="per-instance-pipeline-configuration-using-the-explorer-object-model"></a>Configuration du pipeline par instance à l'aide du modèle objet de l'Explorateur  
 Lorsque le fichier XML décrivant la configuration par instance des composants de pipeline est lu, il remplace les propriétés définies dans le fichier de pipeline.  
  
 La configuration de pipeline par instance est définie à l'aide du modèle objet de l'Explorateur BizTalk. Le modèle d’objet de l’Explorateur BizTalk fournit la **ReceivePipelineData** propriété sur le **IReceiveLocation** et **ISendPort** des interfaces pour la définition de la configuration de composants de pipeline de réception. Le modèle d’objet de l’Explorateur BizTalk fournit également la **SendPipelineData** méthode sur le **IReceivePort** et **ISendPort** des interfaces pour la définition de la configuration d’envoi composants de pipeline.  
  
 La configuration de pipeline par instance ne prend pas en charge ce qui suit :  
  
-   Réorganisation des phases dans le pipeline  
  
-   Ajout ou suppression de phases  
  
-   Réorganisation des composants dans les phases  
  
-   Ajout ou suppression de composants  
  
 Les seules modifications prises en charge font partie de la configuration des composants de pipeline. La configuration par instance d'un composant de pipeline remplace la configuration de composant de pipeline courante. Si le paramètre d'un composant n'est pas spécifié dans la configuration de pipeline par instance, la configuration courante de ce paramètre (telle qu'elle est configurée dans le Concepteur de pipeline) est utilisée.  
  
 Ce qui suit est un exemple de données de configuration par instance.  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<Root xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
    <Stages>  
        <Stage CategoryId="9d0e4103-4cce-4536-83fa-4a5040674ad6">  
            <Components>  
                <Component Name=Microsoft Microsoft.BizTalk.Component.MIME_SMIME_Decoder>  
                    <Properties>  
                        <AllowNonMIMEMessage vt=11>true</AllowNonMIMEMessage>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
        <Stage CategoryId="9d0e4105-4cce-4536-83fa-4a5040674ad6">  
            <Components>  
                <Component Name=Microsoft.BizTalk.Component.XmlDasmComp>  
                    <Properties>  
                        <EnvelopeSpecNames vt=8>MySchemas.EnvelopeSpecNames</EnvelopeSpecNames>  
                        <AllowUnrecognizedMessage vt=11>false</AllowUnrecognizedMessage>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
        <Stage CategoryId="9d0e410d-4cce-4536-83fa-4a5040674ad6" ExecutionSequence="2">  
            <Components>  
                 <Component Name=Microsoft.BizTalk.Component.XmlValidator >  
                    <Properties>  
                        <DocumentSpecName vt=8>MySchemas.DocspecName</DocumentSpecName>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
    </Stages>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md)