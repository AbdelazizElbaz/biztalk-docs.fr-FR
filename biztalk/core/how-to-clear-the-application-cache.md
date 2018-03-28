---
title: Comment faire pour effacer le Cache d’Application | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- caching, applications
- managing [SSO applications], clearing cache
- applications [SSO], caching
ms.assetid: 6230b9a4-c7b8-47b4-854b-12853d9bf5b0
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 184569a3eed693a7b699b2ad14cfb8461cc496e8
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-clear-the-application-cache"></a>Comment faire pour effacer le Cache d’Application
Le composant logiciel enfichable MMC ou l'outil de ligne de commande permet de supprimer le contenu du cache des informations d'identification (c'est-à-dire toutes les informations relatives à l'application qui leur est associée) pour une application spécifique et sur tous les serveurs d'authentification unique.  
  
### <a name="to-clear-the-cache-using-the-mmc-snap-in"></a>Pour effacer le cache à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez sur **Applications associées**.  
  
4.  Dans le volet de résultats, cliquez sur l’application associée, puis cliquez sur **clair**.  
  
### <a name="to-clear-the-cache-using-the-command-line"></a>Pour effacer le cache à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – purgecache *\<nom de l’application\>***, où \<*nom de l’application* \> est le nom de l’application associée vous vous souhaitez purger le cache.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Gestion des applications associées](../core/managing-affiliate-applications.md)