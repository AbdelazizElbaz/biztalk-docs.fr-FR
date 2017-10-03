---
title: "Comment modifier l’emplacement de Destination d’un Script de pré-traitement ou post-traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts, file locations
- scripts, modifying
- managing [scripts], modifying
- managing [scripts], file locations
ms.assetid: 4a4fdaef-099f-4c29-9815-12404c7a2212
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eb4ba338790e301e54a9bf262a49808a0a55315
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-destination-location-of-a-pre--or-post-processing-script"></a>Modification de l'emplacement de destination d'un script de pré-traitement ou de post-traitement
Cette rubrique décrit comment changer l'emplacement de destination d'un script de pré-traitement ou post-traitement à l'aide de la console Administration de BizTalk Server. Il s'agit de l'emplacement de copie du script lors de l'installation de l'application. Vous pouvez être amené à le changer lors du déploiement d'une application dans un autre environnement.  
  
> [!IMPORTANT]
>  Veillez à attribuer un emplacement de destination à un script devant s'exécuter lors de la désinstallation de l'application. Dans le cas contraire, le script ne sera pas copié dans le système de fichiers local et ne pourra pas s'exécuter lors de la désinstallation.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-modify-the-deployment-properties-of-a-pre--or-post-processing-script"></a>Pour modifier les propriétés de déploiement d'un script de pré-traitement ou post-traitement  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk contenant le script à modifier, puis l'application contenant le script.  
  
3.  Cliquez sur le **ressources** dossier, cliquez sur le script, puis cliquez sur **modifier**.  
  
4.  Dans **l’emplacement de Destination**, le chemin d’accès complet de l’emplacement de destination, y compris le nom de fichier, puis tapez **OK**. Vous pouvez utiliser la variable d'environnement %BTAD_InstallDir% dans le chemin d'accès pour spécifier le dossier d'installation de l'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Scripts de pré-traitement et post-traitement](../core/managing-pre-and-post-processing-scripts.md)