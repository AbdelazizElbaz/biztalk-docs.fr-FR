---
title: "Comment configurer les propriétés de Pipeline par instance d’un emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- receive locations, configuring
- managing [pipelines], properties
- managing [pipelines], receive locations
- managing [receive locations], pipelines
- managing [pipelines], configuring
- pipelines, receive locations
- pipelines, configuring
- receive locations, pipelines
- managing [receive locations], configuring
ms.assetid: e1ed3b10-2f39-479b-a3e6-22b4b2872192
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e14483c5d17d968fc79126c65506720b501b6da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-per-instance-pipeline-properties-for-a-receive-location"></a>Configuration des propriétés de pipeline par instance pour un emplacement de réception
Cette rubrique explique comment configurer les propriétés de pipeline d'un port de réception à l'aide de la console Administration de BizTalk Server après le déploiement du pipeline dans un groupe BizTalk. Les modifications que vous effectuez remplacent les propriétés de pipeline par défaut de cet emplacement de réception uniquement. Vous pouvez donc configurer différentes propriétés de pipeline pour chacun des emplacements de réception du groupe BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
> [!NOTE]
>  Lors de l’utilisation des propriétés de pipeline par instance pour définir la valeur de la **DocumentSpecNames** propriété dans le composant désassembleur XML d’un pipeline, le schéma de document spécifié et le pipeline doit être définie dans le même projet.  
  
### <a name="to-configure-per-instance-pipeline-properties-for-a-receive-location"></a>Pour configurer les propriétés de pipeline par instance d'un emplacement de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant l’emplacement de réception pour lequel configurer les propriétés de pipeline, **Applications**, puis Développez l’application contenant l’emplacement de réception.  
  
3.  Cliquez sur le **emplacements de réception** dossier, cliquez sur l’emplacement de réception, puis cliquez sur **propriétés**.  
  
4.  Cliquez sur les points de suspension (...) à droite de la **Pipeline de réception** boîte.  
  
5.  Configurer les propriétés de votre choix, puis cliquez sur **OK**. Pour plus d’informations, cliquez sur **aide** sur la page de propriétés.  
  
    > [!IMPORTANT]
    >  Assurez-vous que les informations de propriétés que vous entrez sont correctes. Si une des valeurs n'est pas valide, par exemple une chaîne au lieu d'un nombre, une erreur est générée.  
  
6.  S’il s’agit d’une requête-réponse emplacement de réception, cliquez sur les points de suspension (...) à droite de la **Pipeline d’envoi** boîte.  
  
7.  Configurer les propriétés de votre choix, puis cliquez sur **OK** à deux reprises. Pour plus d’informations, cliquez sur **aide** sur la page de propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Pipelines](../core/managing-pipelines.md)   
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)   
 [La gestion des emplacements de réception](../core/managing-receive-locations.md)