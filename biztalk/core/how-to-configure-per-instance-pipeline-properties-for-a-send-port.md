---
title: "Comment configurer les propriétés de Pipeline par Instance pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- managing [pipelines], properties
- configuring, send ports
- configuring, pipelines
- managing [pipelines], configuring
- managing [send ports], pipelines
- managing [send ports], configuring
- send ports, pipelines
- pipelines, configuring
ms.assetid: c58faa9e-0dfb-458b-8f1b-d3c91bce0436
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfb9927dca890a7f84baf372c4fa250a8ced17c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-per-instance-pipeline-properties-for-a-send-port"></a>Configuration des propriétés de pipeline par instance pour un port d'envoi
Cette rubrique explique comment configurer les propriétés de pipeline d'un port d'envoi à l'aide de la console Administration de BizTalk Server après le déploiement du pipeline dans un groupe BizTalk. Les modifications que vous effectuez remplacent les propriétés de pipeline par défaut de ce port d'envoi uniquement. Vous pouvez donc configurer différentes propriétés de pipeline pour chacun des ports d'envoi du groupe BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
> [!NOTE]
>  Lors de l’utilisation des propriétés de pipeline par instance pour définir la valeur de la **DocumentSpecNames** propriété dans le composant désassembleur XML d’un pipeline, le schéma de document spécifié et le pipeline doit être définie dans le même projet.  
  
### <a name="to-configure-per-instance-pipeline-properties-for-a-send-port"></a>Pour configurer les propriétés de pipeline par instance d'un port d'envoi  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant le port d’envoi pour lequel vous souhaitez configurer les propriétés de pipeline, **Applications**, puis Développez l’application contenant le port d’envoi.  
  
3.  Cliquez sur le **Ports d’envoi** dossier, cliquez sur le port d’envoi, puis cliquez sur **propriétés**.  
  
4.  Cliquez sur le bouton de sélection (**...** ) situé à droite de la **Pipeline d’envoi** boîte.  
  
5.  Configurer les propriétés de votre choix, puis cliquez sur **OK**. Cliquez sur **aide** sur la page de propriétés pour plus d’informations.  
  
    > [!IMPORTANT]
    >  Assurez-vous que les informations de propriétés que vous entrez sont correctes. Si une des valeurs n'est pas valide, par exemple une chaîne au lieu d'un nombre, une erreur est générée.  
  
6.  S’il s’agit d’un port d’envoi de sollicitation-réponse, cliquez sur le bouton de sélection (**...** ) situé à droite de la **Pipeline de réception** boîte.  
  
7.  Configurer les propriétés de votre choix, puis cliquez sur **OK** à deux reprises. Cliquez sur **aide** sur la page de propriétés pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Pipelines](../core/managing-pipelines.md)   
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)   
 [La gestion des emplacements de réception](../core/managing-receive-locations.md)