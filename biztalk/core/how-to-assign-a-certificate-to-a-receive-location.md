---
title: "Comment attribuer un certificat à un emplacement de réception | Documents Microsoft"
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
ms.assetid: 54ae300e-62c5-480f-a9b7-e5c3457a0f80
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94554aa5781ed609e5129d58ab75e5709e432278
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-a-certificate-to-a-receive-location"></a>Attribution d'un certificat à un emplacement de réception
Cette rubrique décrit comment attribuer un certificat de sécurité à un emplacement de réception à l'aide de la console Administration de BizTalk Server. Cette procédure n'est possible que sur les emplacements de réception bidirectionnels. Le certificat doit figurer dans le magasin de certificats Autres personnes sur l'ordinateur exécutant BizTalk Server, faute de quoi les messages associés à cet emplacement de réception ne seront pas traités et des erreurs seront consignées.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### <a name="to-assign-a-certificate-to-a-receive-location"></a>Pour attribuer un certificat à un emplacement de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle attribuer un certificat à un emplacement de réception.  
  
3.  Développez **emplacements de réception**, avec le bouton droit à l’emplacement de réception, cliquez sur **propriétés**, puis cliquez sur **certificat**.  
  
4.  Si le certificat existe sur l’ordinateur local, cliquez sur **Parcourir**, localisez le certificat que vous souhaitez attribuer à cet emplacement de réception et puis cliquez sur **OK**. Sinon, ignorez cette étape.  
  
    > [!NOTE]
    >  Si vous effectuez cette opération depuis un ordinateur distant, vérifiez que le certificat figure bien sur l'ordinateur exécutant BizTalk Server, et pas seulement sur l'ordinateur local. Sinon, l'emplacement de réception ne pourra pas traiter les messages.  
  
5.  Si le certificat n’existe pas sur l’ordinateur local, dans le **l’empreinte numérique** zone, tapez ou collez l’empreinte numérique du certificat, puis cliquez sur **OK**. Le format de l'empreinte du certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est un nombre hexadécimal.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des emplacements de réception](../core/managing-receive-locations.md)