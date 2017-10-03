---
title: "Réception de PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9acc71ec-05b8-4490-b3ba-0ce7f27a5a6a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11c5add7e71e56f250b95736d97f0434adf72282
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receiving-from-peoplesoft"></a>Réception à partir de PeopleSoft
L'adaptateur Microsoft pour PeopleSoft Enterprise est un adaptateur d'envoi. Il prend en charge les échanges de type sollicitation-réponse et permet d'envoyer une requête et d'obtenir une réponse. Cependant, si vous souhaitez seulement recevoir des données de PeopleSoft, procédez comme suit :  
  
1.  Créez un pipeline de réception personnalisé à l'aide du composant de pipeline Set Namespace.  
  
2.  Créez un port de réception accessible à partir de PeopleSoft, tel qu'un port utilisant un adaptateur HTTP. Utilisez le pipeline de réception personnalisé avec le port de réception.  
  
## <a name="the-set-namespace-pipeline-component"></a>Composant de pipeline Set Namespace  
 Les messages reçus de PeopleSoft n'incluent pas d'espaces de noms. Le composant de pipeline Set Namespace permet d'ajouter un espace de noms à un message entrant.  
  
 L'emplacement par défaut de ce composant de pipeline est C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\Pipeline Component. Vous devez copier le composant Microsoft.BizTalk.Adapters.Pipeline.SetNSForMsg.dll vers le répertoire Composant de pipeline utilisé par BizTalk. Vous devez également ajouter le composant à la boîte à outils de Visual Studio pour pouvoir l'utiliser dans le Concepteur de pipeline.  
  
 Pour plus d’informations sur l’emplacement d’installation du composant, consultez [déploiement des composants de Pipeline](../core/deploying-pipeline-components.md).  
  
 Pour plus d’informations sur l’ajout du composant à la boîte à outils Visual Studio, consultez [l’utilisation de la boîte à outils](../core/how-to-use-the-toolbox.md).  
  
## <a name="configuring-the-set-namespace-pipeline-component"></a>Configuration du composant de pipeline Set Namespace  
 Vous pouvez définir deux propriétés pour ce composant :  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**Par défaut Target Namespace**|Placer un espace de noms fixe dans le message entrant.|  
|**Target Namespace XPath**|Extraire l'espace de noms du message entrant à partir de l'emplacement spécifié par XPath. Si le composant ne trouve aucun espace de noms valide, il consigne un avertissement dans le journal des événements de l'application et il utilise l'espace de noms cible par défaut, si ce dernier est spécifié.|  
  
 Si vous laissez ces deux propriétés vides, le composant n'affecte aucun espace de noms aux messages entrants mais consigne des avertissements dans le journal des événements de l'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’applications](../core/developing-applications4.md)