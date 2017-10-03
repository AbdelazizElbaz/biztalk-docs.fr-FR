---
title: "Sécurisation de la Page ASPX expéditeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASPX pages, protocol rules
- security, ASPX pages
- RNIFSend.aspx
- ASPX pages, security
- protocol rules [ASPX pages]
ms.assetid: 8214e3f5-a8e9-4d71-957d-ed0852035030
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0c5d5ec97d4d4aed862ffc1dbc0d75d0c0430d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="securing-the-sender-aspx-page"></a>Sécurisation de la Page ASPX expéditeur
Cette rubrique décrit comment protéger la page du fichier RNIFSend.aspx à partir de toute utilisation non autorisée. Il existe deux procédures que vous pouvez utiliser :  
  
-   Dans Gestionnaire des Services Internet (IIS), sécurisez le fichier RNIFSend.aspx pour vous assurer qu’aucun serveur non autorisé n’utilise la page de fichier RNIFSend.aspx pour transmettre des messages non autorisés de votre réseau.  
  
-   Utilisez Microsoft Internet Security and Acceleration (ISA) Server pour créer une règle de protocole de demandes HTTP sortantes.  
  
### <a name="to-secure-rnifsendaspx"></a>Pour sécuriser le fichier RNIFSend.aspx  
  
1.  Sur le serveur Web que vous utilisez pour la transmission de message RNIF, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur  **Internet Information Services (IIS) Manager**.  
  
2.  Dans le Gestionnaire IIS, développez le nœud ordinateur local, **Sites Web**, puis développez **Site Web par défaut**.  
  
3.  Cliquez sur **btarnapp fait**et, dans le volet droit, cliquez sur **fichier RNIFSend.aspx**.  
  
4.  Cliquez sur **Propriétés**. Sur le **sécurité du fichier** sous l’onglet du **restrictions de nom de domaine et les adresses IP** , cliquez sur **modifier**.  
  
5.  Dans la boîte de dialogue adresse IP et les Restrictions de nom de domaine, cliquez sur **accès refusé**, puis cliquez sur **ajouter**.  
  
6.  Dans le **accorder l’accès** boîte de dialogue Ajouter des serveurs BizTalk toutes les opérations d’envoi. Si vous ajoutez un serveur unique, cliquez sur **seul ordinateur**. Dans le **adresse IP** zone, tapez l’adresse IP de l’ordinateur, puis cliquez sur **OK**.  
  
7.  Si vous ajoutez un groupe de serveurs, cliquez sur **groupe d’ordinateurs**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**ID de réseau**|Tapez le réseau que vous souhaitez utiliser.|  
    |**Masque de sous-réseau**|Tapez le masque de sous-réseau que vous souhaitez utiliser.|  
  
8.  Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si vous avez réparti vos opérations d’envoi à un hôte distinct en cours d’exécution sur une instance distincte, vous devez uniquement ajouter cet ordinateur. Vous pouvez refuser tous les autres accès.  
  
9. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
### <a name="to-create-a-protocol-rule-of-outgoing-http-requests"></a>Pour créer une règle de protocole de demandes HTTP sortantes  
  
1.  Dans Gestion ISA, cliquez sur **la stratégie d’accès**, puis cliquez sur **les règles de protocole**.  
  
2.  Créer une nouvelle règle de protocole nommée **HTTP** qui utilise le protocole TCP.  
  
3.  Dans la page de propriétés de votre HTTP nouvelle règle, de protocole dans la **s’applique à** onglet, sélectionnez **s’applique à des ensembles d’adresses Client spécifiés ci-dessous**. Entrez uniquement les adresses IP que vous souhaitez accéder à la page client.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md)