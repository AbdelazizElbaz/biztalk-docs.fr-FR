---
title: Adresse non valide (uri relatif) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a953f3e-3768-4e61-8f25-ea958a5a701a
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 101a4544a83eb02438478d6d526dba422c44ae7b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-address-relative-uri"></a>Adresse non valide (Uri relatif)
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|000|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Schéma d'adresse non valide ; schéma « {0} » attendu.|  
  
## <a name="explanation"></a>Explication  
 L'adresse relative fournie pour l'emplacement de réception WCF isolé n'est pas bien formée. Par exemple, http://localhost/svc n'est pas une adresse relative correcte. Vous ne pouvez pas définir la propriété Adresse de l'emplacement de réception WCF isolé sur une adresse absolue.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer l'adresse de l'emplacement de réception.  
  
#### <a name="to-configure-the-receive-location-address"></a>Pour configurer l'adresse de l'emplacement de réception  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.  
  
3.  Localisez votre application et du localiser votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.  
  
9. Dans le **adresse (URI)** texte, changez l’adresse afin qu’elle commence par une barre oblique (« / »).  
  
 Pour plus d'informations sur les emplacements de réception, consultez les ressources suivantes :  
  
-   [Pour configurer les emplacement de réception WCF-CustomIsolated](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [Pour configurer les emplacement de réception WCF-WSHttp](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [Pour configurer les emplacement de réception WCF-BasicHttp](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)