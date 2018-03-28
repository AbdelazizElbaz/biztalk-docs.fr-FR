---
title: Comment faire pour effacer le Cache d’Application | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a897791-d32f-46a4-8c5d-2b2161e92bd9
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 24954e8314bc94d4570eb57acbf1d4b03bebb65b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-clear-the-application-cache"></a>Comment faire pour effacer le Cache d’Application
Utilisez le composant logiciel enfichable MMC ou la **purgecache** commande pour supprimer le contenu du cache d’informations d’identification (toutes les informations associé à l’application associée) pour l’application spécifiée sur tous les serveurs Single Sign-On (SSO).  
  
### <a name="to-clear-the-cache-using-the-mmc-snap-in"></a>Pour effacer le cache à l'aide du composant logiciel enfichable MMC  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez sur **Applications associées**.  
  
4.  Dans le volet de résultats, cliquez sur l’application associée, puis cliquez sur **clair**.  
  
### <a name="to-clear-the-cache-using-the-command-line"></a>Pour effacer le cache à l'aide de la ligne de commande  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –purgecache <application name>`, où \< *nom de l’application*> est le nom de l’application associée que vous souhaitez purger le cache.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../esso/sso-affiliate-applications.md)   
 [Gestion des applications associées](../esso/managing-affiliate-applications.md)