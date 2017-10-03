---
title: Comment configurer des certificats avec un adaptateur SOAP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20ee05c5-9cea-456d-bff6-49dd249f0ff4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e382fa9084fd728e04efa29900fb0222d8b05ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-with-a-soap-adapter"></a>Comment configurer des certificats avec un adaptateur SOAP
L’adaptateur d’envoi SOAP peut aider à sécuriser une connexion avec les serveurs qui acceptent ou demandent des certificats clients. Si un certificat client est spécifié, l'adaptateur d'envoi SOAP utilise le certificat lors de la connexion aux serveurs qui demandent ou acceptent des certificats clients. Si vous ne spécifiez pas un certificat client et le serveur de destination requiert des certificats clients, l’expéditeur n’est pas authentifié et l’envoi SOAP adaptateur ne parvient pas à envoyer le message et suit la logique de nouvelle tentative standard.  
  
 L'adaptateur d'envoi SOAP utilise le certificat client du magasin Personnel du compte sous lequel le processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté. L'adaptateur SOAP spécifie le certificat par son empreinte. Si l'adaptateur d'envoi SOAP ne peut pas charger le certificat pour une raison quelconque, le message envoyé est interrompu.  
  
 Lorsque vous utilisez un adaptateur SOAP pour envoyer un message signé ou chiffré, configurez la propriété de transport SOAP empreinte de certificat Client pour le port d’envoi.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
### <a name="to-configure-biztalk-server-to-send-messages-over-a-soap-connection"></a>Pour configurer BizTalk Server pour envoyer des messages via une connexion SOAP  
  
1.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, créez un port d’envoi SOAP ou ouvrez les propriétés de port d’envoi un SOAP existante.  
  
2.  Cliquez sur **configurer** dans les **Transport** section de la **propriétés de Port d’envoi** boîte de dialogue.  
  
3.  Sur le **général** sous l’onglet **type d’authentification**, sélectionnez **anonyme**, **base**, **Digest**, ou **NTLM**.  
  
4.  Si le type d’authentification est **base** ou **Digest**, sélectionnez **n’utilisez pas l’authentification unique sur** (auquel cas vous devez spécifier le nom d’utilisateur et un mot de passe) ou sélectionnez  **Utiliser l’authentification unique sur** (auquel cas vous devez sélectionner l’Application associée).  
  
5.  Dans **l’empreinte numérique du certificat SSL client**, entrez l’empreinte numérique approprié.  
  
6.  Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.