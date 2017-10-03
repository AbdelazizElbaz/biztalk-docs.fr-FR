---
title: Comment supprimer SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, deleting
- SSO, deleting
- deleting, SSO
- deleting, Master Secret server
ms.assetid: 0e1ad8e3-0938-4f36-b85b-4631d0eeb8c9
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7134186161c3c0647a20047afcbbe317fcbad1ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-sso"></a>Comment supprimer l’authentification unique
Si vous supprimez BizTalk Server, l'authentification unique de l'entreprise (SSO) n'est ni configurée (sauf si un produit dépendant l'utilise), ni supprimée. Vous devez donc supprimer SSO séparément. Vous pouvez également restaurer les informations de configuration, y compris le secret principal, afin de réutiliser les données existantes. Pour plus d’informations, consultez [comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md).  
  
### <a name="to-remove-enterprise-single-sign-on"></a>Pour supprimer l'authentification unique de l'entreprise  
  
1.  Sauvegardez la clé du secret principal. Pour plus d’informations, consultez [comment revenir Up the Master Secret](../core/how-to-back-up-the-master-secret.md).  
  
2.  Désinstallez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
3.  Dans le menu **Démarrer** , cliquez sur **Panneau de configuration**.  
  
4.  Cliquez sur **Ajout/Suppression de programmes**.  
  
5.  Dans le **Ajout/Suppression de programmes** boîte de dialogue, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **supprimer**.  
  
6.  Cliquez sur **Oui** lorsque vous êtes invité à confirmer la suppression de Microsoft Enterprise Single Sign-On.  
  
    > [!NOTE]
    >  Si les composants d'exécution, de développement ou d'administration BizTalk Server ou les fonctionnalités d'administration Host Integration Server ne sont pas installés, vous ne pouvez pas désinstaller les composants d'administration ou d'exécution de l'authentification unique tant que toutes les dépendances n'ont pas été désinstallées.  
  
## <a name="see-also"></a>Voir aussi  
 [L’installation de l’authentification unique](../core/installing-sso.md)