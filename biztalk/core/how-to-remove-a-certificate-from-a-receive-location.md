---
title: "Comment supprimer un certificat d’un emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, receive locations
- receive locations, certificates
- managing [receive locations], certificates
ms.assetid: 717d41bf-4260-4df4-9d0a-07243bb9b12c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e70cd846c364d52544bf8504d42132dd35fe65d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-certificate-from-a-receive-location"></a>Suppression d'un certificat d'un emplacement de réception
Cette rubrique décrit comment supprimer un certificat de sécurité d'un emplacement de réception à l'aide de la console Administration de BizTalk Server. Une fois cette opération effectuée, l'emplacement de réception ne chiffrera plus les messages. Ils seront désormais envoyés en texte clair. Supprimer un certificat d'un emplacement de réception ne le supprime pas automatiquement du magasin de certificats.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-remove-a-certificate-from-a-receive-location"></a>Pour supprimer un certificat d'un emplacement de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend l'emplacement de réception dans lequel supprimer un certificat.  
  
3.  Développez **emplacements de réception**, avec le bouton droit à l’emplacement de réception, cliquez sur **propriétés**, puis cliquez sur **certificats**.  
  
4.  Cliquez sur **supprimer le certificat**, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des emplacements de réception](../core/managing-receive-locations.md)