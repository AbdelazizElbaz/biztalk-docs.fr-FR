---
title: "Échec de création de X509CertificateIdentity à partir de la référence de certificat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3acee8e-c035-4e58-8bfc-397885b4d185
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c6bb03698010d667b27334f17fa7270de845c68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="failed-to-create-x509certificateidentity-from-certificate-reference"></a>Échec de création de X509CertificateIdentity à partir de la référence du certificat
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Échec de création de X509CertificateIdentity à partir de la référence du certificat. (StoreName = {0}, StoreLocation = \ {1\\}, X509FindType = \ {2\}, FindValue = "\ {3\} »)|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que l'adaptateur n'a pas pu créer le X509Certificate spécifié pour la configuration de l'identité du point de terminaison.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de vérifier les paramètres de la référence de certificat.  
  
#### <a name="to-configure-the-certificate-reference-settings"></a>Pour configurer les paramètres de la référence de certificat  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.  
  
9. Dans le **identité du point de terminaison** , cliquez sur **modifier.**  
  
10. Dans le **Éditeur d’identités** boîte de dialogue zone, vérifiez que le **référence du certificat** les paramètres sont valides.