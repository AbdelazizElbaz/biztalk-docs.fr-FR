---
title: "Adresse de proxy non valide (pour le port d’envoi et de gestionnaire d’envoi) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccedd23e-7d44-4419-b519-e04511e1f176
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d33af2f4fa068294c38ecb4146cd1f8d05d68aea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-proxy-address-for-send-handler-and-send-port"></a>Adresse de proxy non valide (pour le port et le gestionnaire d'envoi)
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Adresse de proxy non valide : {0}|  
  
## <a name="explanation"></a>Explication  
 Le gestionnaire d'envoi WCF ou le port d'envoi WCF fourni ne possède pas d'adresse de proxy valide.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer une adresse de proxy.  
  
#### <a name="to-configure-a-proxy-address"></a>Pour configurer une adresse de proxy  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **Proxy** onglet.  
  
9. Vérifiez que l’adresse proxy dans le **paramètres Proxy** section est correctement configurée.  
  
 Pour plus d'informations sur les ports et gestionnaires d'envoi, consultez les ressources suivantes :  
  
-   [Comment configurer un Port d’envoi WCF-WSHttp](../core/how-to-configure-a-wcf-wshttp-send-port.md)  
  
-   [Comment configurer un Port d’envoi WCF-BasicHttp](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f)  
  
-   [Comment configurer un gestionnaire d’envoi WCF-BasicHttp](http://msdn.microsoft.com/library/18dcc616-4732-42f8-bd64-e55a5ebbaa49)  
  
-   [Comment configurer un gestionnaire d’envoi WCF-WSHttp](../core/how-to-configure-a-wcf-wshttp-send-handler.md)  
  
-   [Comment configurer un Port d’envoi WCF-Custom](../core/how-to-configure-a-wcf-custom-send-port.md)