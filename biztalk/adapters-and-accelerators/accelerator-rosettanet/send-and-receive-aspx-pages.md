---
title: Envoyer et recevoir des Pages ASPX | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTARN, ASPX pages
- ASPX pages, initiator
- HTTP adapters
- connections, HTTP adapters
- connections, single-action
- ASPX pages, responder
- single-action connections
- RNIFSend.aspx
- connections, asynchronous
- ASPX pages, about ASPX pages
- double-action connections
- connections, synchronous
- connections, double-action
- ASPX pages
- HTTP adapters, connections
- asynchronous connections
- RNIFReceive.aspx
- synchronous connections
ms.assetid: 21e52390-35d8-44b1-a5cd-1cd60cfe6e61
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6e7f5f215ec2fc3dc85f88ed54ab22280a81fd0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-and-receive-aspx-pages"></a>Envoyer et recevoir des Pages ASPX
Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] les pages ASPX sont les interfaces directes entre [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] et Internet. Les deux pages ASPX sont la page de réception (RNIFReceive.aspx) et de la page d’envoi (fichier RNIFSend.aspx). Chaque page ASPX est une extension correspondant [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline. Le pipeline nécessite la page ASPX pour gérer les en-têtes de Framework RNIF (RosettaNet Implementation). Le pipeline exécute la plupart du HTTP traitement ; Toutefois, chaque page ASPX effectue le traitement des en-têtes de RNIF HTTP. Les pages de compléter les fonctionnalités dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adaptateur HTTP.  
  
 Chaque page ASPX est une page ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] application sans interface utilisateur Web. Utiliser des pages ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] Web sécurité pour garantir une connexion sécurisée avec des tiers externes. Ils fournissent une couche dans laquelle vous pouvez implémenter la tolérance de panne, d’évolutivité et de services hautement disponibles.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]le programme d’installation installe une page de fichier RNIFSend.aspx et d’une page de fichier RNIFReceive.aspx sur chaque déploiement de [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]. Lorsque l’initiateur ou répondeur échange des messages avec le partenaire commercial, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] utilise les pages ASPX pour envoyer des messages ou recevoir des messages à partir de l’URL du partenaire. Si l’initiateur et le répondeur utilisent [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], les deux pages ASPX sur l’initiateur échangent des messages avec les deux pages ASPX sur le répondeur. Pour plus d’informations, voir le « comment initiateur et répondeur ASPX Pages interagissent » de la sous-section ci-dessous.  
  
## <a name="send-aspx-page"></a>Envoyer la Page ASPX  
 La page du fichier RNIFSend.aspx reçoit un message à partir de l’adaptateur HTTP BizTalk. Il crée et ajoute des en-têtes RNIF au message et envoie ensuite le message au partenaire via Internet. L’adaptateur HTTP appelle fichier RNIFSend.aspx avec la commande suivante :  
  
```  
http://localhost:<port number>/RNIFSend.aspx?<query string>  
```  
  
 La chaîne de requête inclut les données suivantes qui a besoin de la page d’envoi pour envoyer le message au partenaire et les données que le partenaire doit avoir pour traiter le message :  
  
-   L’URL de partenariat commercial : http://www. \< *adresse*>.com/RNIFReceive.aspx  
  
-   Le type de réponse : synchronisation ou async  
  
-   La version RNIF : 1.1 ou 2.0.  
  
 L’adaptateur HTTP BizTalk envoie un message MIME produit par le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipeline d’envoi à la page du fichier RNIFSend.aspx initiateur. Fichier RNIFSend.aspx traite le message comme suit :  
  
1.  La page d’envoi exécute une validation sur le message.  
  
2.  La page d’envoi crée un en-tête MIME Multipurpose Internet Mail Extensions () en fonction du type de contenu, la longueur, l’ID et la version MIME. Il ajoute l’en-tête MIME et limites MIME supérieures et inférieures, dans le message.  
  
3.  Pour RNIF 2.01, la page d’envoi définit les propriétés de l’en-tête HTTP comme suit :  
  
    1.  Il définit la propriété de la Version X-RN vers la version entrée dans la propriété de Version des paramètres de configuration de processus.  
  
    2.  Il définit la propriété X-RN-ResponseType synchronisation ou async, selon la valeur de la propriété IsSynchronous dans les paramètres de configuration de processus.  
  
    3.  Il définit la propriété Content-Length à la taille de la totalité du message.  
  
4.  À l’aide d’une requête HTTP Post, la page d’envoi envoie le message à l’URL de destination du partenaire, comme défini dans les paramètres d’URL d’Action ou de Signal dans l’accord de partenariat commercial.  
  
5.  La page d’envoi attend la réponse HTTP. Lorsqu’il reçoit la réponse, il achemine vers l’adaptateur HTTP.  
  
6.  Si la connexion est asynchrone, la page d’envoi ferme la connexion, et son traitement est terminé.  
  
7.  Si la connexion est synchrone, la page d’envoi laisse la connexion ouverte pour un message retourné. Après avoir reçu le message, il effectue le traitement de même qu’une page RNIFReceive.aspx effectue sur un message reçu, envoie le message reçu à l’adaptateur HTTP, puis ferme la connexion.  
  
## <a name="receive-aspx-page"></a>Réception Page ASPX  
 La page RNIFReceive.aspx reçoit un message HTTP du partenaire via Internet. Il traite, valide, puis supprime les en-têtes RNIF et envoie le message à l’adaptateur HTTP. Le message reçu par la page de réception doit être HTTP RNIF transport compatible. La page de réception traite les messages comme suit :  
  
1.  La page de fichier RNIFReceive.aspx répondeur reçoit le message de l’initiateur. Le message contient l’en-tête MIME et les limites supérieures et inférieures.  
  
2.  La page de réception valide l’en-tête MIME.  
  
3.  La page de réception supprime l’en-tête MIME et les limites à partir du message.  
  
4.  La page de réception envoie le message à l’adaptateur HTTP à l’aide de l’emplacement de réception HTTP. La page de réception reçoit une réponse HTTP et retourne la réponse HTTP à la page de l’envoi de l’initiateur.  
  
5.  Si la connexion est asynchrone, la page de réception ferme la connexion.  
  
6.  Si la connexion est synchrone, la page de réception conserve la connexion ouverte, en attendant le message retourné.  
  
7.  Après avoir reçu le message retourné à partir de l’adaptateur HTTP, la page de recevoir le même traitement qui effectue une page de fichier RNIFSend.aspx et envoie le message retourné à la page d’envoi initiateur. Après avoir reçu la réponse HTTP, il ferme la connexion.  
  
## <a name="how-initiator-and-responder-aspx-pages-interact"></a>Interagissent entre les Pages ASPX initiateur et le répondeur  
 Si l’initiateur et le répondeur utilisent [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], les quatre pages ASPX sur l’initiateur et le répondeur interagissent différemment selon si les connexions sont asynchrones ou synchrones, et si les messages sont une action unique ou double action . Les sous-sections suivantes décrivent l’ensemble complet des interactions.  
  
 **Double Action asynchrone**  
  
 Ce scénario implique quatre connexions HTTP distinctes, une pour chaque étape :  
  
1.  Page de réception l’envoie de page initiateur envoyer la demande d’action du message au répondeur.  
  
    > [!NOTE]
    >  Les étapes 2 et 3 ci-dessous peuvent se produire dans l’ordre inverse, en fonction de la charge du système.  
  
2.  Page de réception l’envoie de page répondeur envoyer un signal de demande de message à l’initiateur.  
  
3.  Page de réception l’envoie de page répondeur envoyer une réponse de l’action de message à l’initiateur.  
  
4.  Page de réception l’envoie de page initiateur envoyer un signal de réponse de message au répondeur.  
  
 **Action unique asynchrone**  
  
 Ce scénario implique deux connexions HTTP distinctes, une pour chaque étape. Notez que ce scénario se compose de l’étape 1 et 2 du scénario double action asynchrone.  
  
1.  Page de réception l’envoie de page initiateur envoyer la demande d’action du message au répondeur.  
  
2.  Page de réception l’envoie de page répondeur envoyer un signal de demande de message à l’initiateur.  
  
 **Double Action synchrone**  
  
 Ce scénario implique une connexion HTTP :  
  
1.  Page de réception l’envoie de page initiateur envoyer la demande d’action du message au répondeur.  
  
2.  Le répondeur de réception page envoie un message de réponse d’action (ou une exception, s’il existe un problème) à la page d’envoi initiateur sur la même connexion que celui utilisée à l’étape 1.  
  
 **Action unique synchrone**  
  
 Ce scénario implique une connexion HTTP :  
  
1.  Page de réception l’envoie de page initiateur envoyer la demande d’action du message au répondeur.  
  
2.  Le répondeur de réception page envoie un message de signal de demande (ou une exception, s’il existe un problème) à la page d’envoi initiateur sur la même connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages dans BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)   
 [Pipeline de réception BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)   
 [Pipeline d’envoi BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)