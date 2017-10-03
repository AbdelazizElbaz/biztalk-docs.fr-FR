---
title: "Comment configurer un gestionnaire d’envoi SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send handlers, SOAP adapters
- SOAP adapters, denial of service
- denital of service, HTTP adapters
- configuring [SOAP adapters], send handlers
- configuring [SOAP adapters], denial of service
- SOAP adapters, send handlers
- denial of service, SOAP adapters
ms.assetid: fd610a3f-ca10-42e0-b81e-219e07e33830
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65ca116b47e36d754b27839a09225aeb313c9e0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-soap-send-handler"></a>Comment configurer un gestionnaire d’envoi SOAP
La procédure suivante permet de configurer le gestionnaire d'envoi SOAP.  
  
> [!CAUTION]
>  Lorsque vous utilisez des gestionnaires d’adaptateur HTTP ou SOAP, il est recommandé d’installer les instances d’hôte pour ces gestionnaires sur Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]ordinateurs.  
  
### <a name="to-change-global-variables-for-a-soap-send-handler"></a>Pour modifier des variables globales d'un gestionnaire d'envoi SOAP  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **SOAP**, dans le volet de droite, avec le bouton du Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel associer le Gestionnaire de réception.  
  
4.  Sur le **Proxy** onglet, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Utiliser le proxy**|Indiquer si le gestionnaire d'envoi SOAP fait appel ou non à un serveur proxy.|  
    |**Server**|Indiquer le nom du serveur proxy.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> Type : Chaîne<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
    |**Port**|Indiquer le port que le gestionnaire d'envoi SOAP utilise.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> Valeur par défaut : 80<br /><br /> Type : Long<br /><br /> Valeur minimale : 0<br /><br /> Valeur maximale : 65535|  
    |**Nom d'utilisateur**|Indiquer le nom d’utilisateur nécessaire à l’authentification.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> Type : Chaîne<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
    |**Mot de passe**|Indiquer le mot de passe nécessaire à l’authentification.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> Type : Chaîne<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur SOAP](../core/configuring-the-soap-adapter.md)   
 [Publication de Services Web](../core/publishing-web-services.md)