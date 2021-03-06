---
title: "Impossible de créer l’élément de configuration de comportement de point de terminaison à partir de la configuration XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89d906a4-ea85-42d8-8e9e-0a3a7774bcd8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc10a737f2c0a2f344a106868c910a2ecb8144bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-endpoint-behavior-configuration-element-from-xml-configuration"></a>Impossible de créer l'élément de configuration du comportement du point de terminaison à partir de la configuration XML.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible de créer l'élément de configuration du comportement du point de terminaison à partir de la configuration XML.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que l'adaptateur n'a pas chargé la configuration du comportement du point de terminaison. Cette situation se produit essentiellement avec les adaptateurs WCF-Custom et WCF-CustomIsolated.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de configurer le comportement du point de terminaison.  
  
#### <a name="to-configure-the-endpoint-behavior"></a>Pour configurer le comportement du point de terminaison  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **comportement** onglet.  
  
9. Dans le **comportement** section, vérifiez le **EndpointBehavior** configuration.