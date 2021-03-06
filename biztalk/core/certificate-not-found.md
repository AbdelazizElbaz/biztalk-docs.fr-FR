---
title: Certificat introuvable | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 629b199f-1884-4e88-beaa-a2e5c5e792e9
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1c18f112edc14375e6edc2aaa52c9e468d1bd39
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="certificate-not-found"></a>Certificat introuvable
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Certificat introuvable.|  
  
## <a name="explanation"></a>Explication  
 Aucun certificat correspondant aux critères de recherche n'a été trouvé.  

#### <a name="user-action"></a>Action de l'utilisateur
Vérifiez les critères de recherche de certificats. 
  
## <a name="verify-search-criteria"></a>Vérifier les critères de recherche  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.  
  
9. Cliquez sur **Modifier**.  
  
10. Dans le **Éditeur d’identités** boîte de dialogue zone, assurez-vous que les critères de recherche dans les **référence du certificat** section est correctement configurée pour indiquer des certificats valides.  
  
 Pour WCF-Custom et les adaptateurs WCF-CustomIsolated, vérifiez que les critères de recherche dans les **référence du certificat** section est correctement configurée pour indiquer un certificat valide dans le certificat **nom de magasin** .  
  
## <a name="verify-search-criteria-for-standard-wcf-adapters"></a>Vérifier les critères de recherche pour les adaptateurs WCF standards  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **sécurité** onglet.  
  
9. Vérifiez que le **l’empreinte numérique** propriétés pour les certificats de client et service indiquent des certificats valides dans les magasins de certificats.  
  
10. Dans le composant logiciel enfichable Certificat, vérifiez que des certificats valides sont installés pour le transport WCF.  

## <a name="see-also"></a>Voir aussi 
  
-   [Installation des certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md)  
  
