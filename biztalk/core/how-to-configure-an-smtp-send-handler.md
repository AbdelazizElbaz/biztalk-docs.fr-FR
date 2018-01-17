---
title: "Comment configurer un gestionnaire d’envoi SMTP | Documents Microsoft"
ms.custom: 
ms.date: 2015-10-22
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send handlers, SMTP adapters
- SMTP adapters, send handlers
- configuring [SMTP adapters], send handlers
ms.assetid: b68a36ce-f0a5-4302-a405-bb154c935f47
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99dc71cf04d8a80b3a88630908a814957c83b8cb
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-configure-an-smtp-send-handler"></a>Comment configurer un gestionnaire d’envoi SMTP
Vous pouvez définir les propriétés du gestionnaire d'envoi SMTP dans la console Administration de BizTalk. Ces propriétés du gestionnaire d'envoi sont utilisées comme valeurs de configuration du port d'envoi si les propriétés ne sont pas définies sur le port d'envoi SMTP individuel.  
  
### <a name="to-change-global-variables-for-an-smtp-send-handler"></a>Pour modifier des variables globales d'un gestionnaire d'envoi SMTP  
  
1.  Dans la Console Administration de BizTalk Server, développez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Adaptateurs**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **SMTP**, dans le volet de droite, avec le bouton du Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet le **nom d’hôte** , sélectionnez l’hôte avec lequel le Gestionnaire d’envoi est associé et puis cliquez sur **Propriétés**.  
  
4.  Dans le **propriétés du Transport SMTP** boîte de dialogue le **propriétés** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom du serveur SMTP et le port TCP**|**[!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)]**<br /><br /> Obligatoire. Entrez le nom du serveur SMTP et le numéro de port TCP (facultatif) à utiliser lors de l’envoi de messages. Par exemple, vous pouvez entrer :<br /><br /> -   mySMTPserver<br />-   mySMTPserver.internet.com:2525<br /><br /> **Dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**  (y compris de BizTalk Server 2013), entrez uniquement le nom du serveur SMTP. Port TCP 25 est codé en dur.<br /><br /> Longueur maximale : 256|  
    |**À partir de (adresse de messagerie)**|Obligatoire. Entrez l’adresse de messagerie à placer sur le protocole SMTP **de** en-tête.<br /><br /> Longueur maximale : 256|  
    |**Type d'authentification**|Entrez le type d’authentification à utiliser avec le serveur SMTP.<br /><br /> Options :<br /><br /> -   **Aucune authentification**<br />-   **Authentification de base**<br />-   **Compte du processus (NTLM)**<br /><br /> Valeur par défaut : compte (NTLM) de processus|  
    |**Nom d'utilisateur**|Entrez le nom d’utilisateur à utiliser pour l’authentification avec le serveur SMTP.<br /><br /> Cette propriété exige une valeur si **type d’authentification** est **l’authentification de base**.<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
    |**Mot de passe**|Entrez le mot de passe à utiliser pour l’authentification avec le serveur SMTP.<br /><br /> Cette propriété exige une valeur si **type d’authentification** est **l’authentification de base**.<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur SMTP](../core/configuring-the-smtp-adapter.md)