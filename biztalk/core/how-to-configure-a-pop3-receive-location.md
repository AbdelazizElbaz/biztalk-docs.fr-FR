---
title: "Pour configurer les emplacement de réception POP3 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, POP3 adapters
- POP3 adapters, receive locations
- configuring [POP3 adapters], receive locations
ms.assetid: 259cd105-733a-4f87-be30-c02e6bd0f457
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 410bfed33402d8d810434e7ff9287fa5c01462da
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-a-pop3-receive-location"></a>Pour configurer les emplacement de réception POP3
Vous pouvez définir des variables d'adaptateur d'emplacement de réception POP3 dans la console Administration de BizTalk Server. Si les propriétés ne sont pas définies pour l'emplacement de réception, les valeurs par défaut du gestionnaire de réception définies dans la console Administration de BizTalk Server sont utilisées.  
  
> [!NOTE]
>  Avant d'effectuer la procédure suivante, vous devez avoir ajouté un port de réception. Pour plus d’informations, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
 **Pour configurer l’emplacement de réception variables pour POP3**  
  
1.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le vous souhaitez créer un emplacement de réception dans l’application.  
  
2.  Dans la console Administration de BizTalk Server, dans le volet gauche, cliquez sur le **Port de réception** nœud. Dans le volet droit, cliquez avec le bouton droit sur le port de réception associé à un emplacement de réception existant ou auquel associer un nouvel emplacement, puis cliquez sur **Propriétés**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**, puis dans le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau**pour créer un nouvel emplacement de réception.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section regard **Type**, sélectionnez **POP3** dans la liste déroulante, puis cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport POP3** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Appliquer le décodage MIME**|Indiquer s'il faut appliquer le décodage MIME aux messages que reçoit l'adaptateur POP3. Le décodage MIME permet d'analyser le message entrant et les éventuelles pièces jointes à des fins de conversion en message BizTalk en plusieurs parties. **Important :** si cette valeur est définie sur `False` puis l’adaptateur POP3 envoie le corps du message dans son intégralité, y compris les en-têtes de message à BizTalk Server. <br /><br /> Valeur par défaut :`True`|  
    |**Type de contenu du corps**|Indiquer le type de contenu du corps des messages électroniques entrants à envoyer à BizTalk Server. Il s’agit d’un paramètre facultatif. Consultez [quel est l’adaptateur POP3 ?](../core/what-is-the-pop3-adapter.md) pour plus d’informations.|  
    |**Index du corps**|Indiquer l'index du corps des messages électroniques entrants à envoyer à BizTalk Server. Consultez [quel est l’adaptateur POP3 ?](../core/what-is-the-pop3-adapter.md) pour plus d’informations.<br /><br /> Valeur par défaut : 0|  
    |**Serveur de messagerie**|Indiquer le serveur de messagerie POP3 sur lequel réside la boîte aux lettres qui sera interrogée par l'adaptateur POP3. **Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**Port**|Indiquer le port du serveur POP3.<br /><br /> Valeurs valides : entre 1 et 65535 compris.<br /><br /> Valeur par défaut : 0 **Remarque :** la valeur 0 indique l’utilisation du port POP3 par défaut 110 si **utiliser SSL** est `False` ou port 995 si **utiliser SSL** est `True`.|  
    |**Schéma d’authentification**|Indiquez le type d'authentification à utiliser avec le serveur de destination.<br /><br /> Les options admises sont les suivantes :<br /><br /> -   **Base**<br />-   **Digest**<br />-   **SPA** **Remarque :** lorsque vous utilisez l’authentification SPA est utilisée, le nom d’utilisateur doit être spécifié avec l’un des formats suivants : les comptes de domaine doivent être entrés avec la syntaxe : \<nom de domaine\> \\< nom d’utilisateur\> les comptes locaux doivent être entrés avec la syntaxe : \<nom de l’ordinateur\>\\< nom d’utilisateur\>|  
    |**Mot de passe**|Indiquer le mot de passe utilisateur nécessaire à l'authentification sur le serveur POP3.|  
    |**Utiliser SSL**|Indiquez s'il faut utiliser une connexion SSL (Secure Sockets Layer) pour communiquer avec le serveur de destination.<br /><br /> Valeur par défaut :`False`|  
    |**Nom d'utilisateur**|Indiquer le nom d'utilisateur nécessaire à l'authentification sur le serveur POP3. Cette propriété exige une valeur. **Remarque :** le compte spécifié pour la propriété de nom d’utilisateur doit avoir la possibilité d’ouvrir une session sur le réseau. L'adaptateur POP3 se connecte à la boîte aux lettres associée au compte spécifié pour la propriété de nom d'utilisateur. C'est pourquoi, il est impossible d'utiliser l'adaptateur POP3 pour se connecter à une boîte aux lettres autre que celle affectée au compte spécifié. Par exemple, même si plusieurs comptes disposent d'autorisations de lecture pour la boîte aux lettres associée à un compte spécifique, seul le nom de compte réel peut être spécifié comme nom d'utilisateur.|  
    |**Seuil d’erreur**|Indiquer le nombre maximal d'erreurs réseau ou de protocole devant être rencontrées avant que l'adaptateur ne soit fermé. Pour empêcher l'adaptateur de fermer, indiquer la valeur 0.<br /><br /> Valeur par défaut : 10|  
    |**Intervalle d’interrogation**|Indiquer l'intervalle avant nouvelle tentative de récupération des messages du serveur POP3.<br /><br /> Valeur par défaut : 5|  
    |**Unité d’intervalle d’interrogation**|Spécifiez l’unité de mesure à utiliser pour le **fréquence d’interrogation**.<br /><br /> Valeur par défaut : Minutes|  
  
6.  Cliquez sur **OK**.  
  
7.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, entrez les valeurs appropriées pour terminer la configuration de l’emplacement de réception, puis cliquez sur **OK** pour enregistrer les paramètres. Pour plus d’informations sur la **propriétés des emplacements de réception** boîte de dialogue, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
> [!NOTE]
>  L'adaptateur POP3 génèrera une erreur et ne réussira pas à traiter les messages si la boîte aux lettres qu'il doit lire inclut plus de 2 147 483 647 messages électroniques. L'adaptateur POP3 stocke le nombre de messages de la boîte aux lettres qu'il doit lire dans une variable Int32 et la valeur maximale pour le type de données Int32 est 2 147 483 647.  
  
> [!IMPORTANT]
>  Lorsque l'adaptateur POP3 a réussi à récupérer un message électronique d'une boîte aux lettres cible, il le supprime de celle-ci. Ce comportement par défaut empêche l'adaptateur POP3 de récupérer plusieurs copies d'un message électronique. Ne configurez pas un emplacement de réception POP3 pour surveiller une boîte aux lettres si vous ne souhaitez pas que les messages électroniques de celle-ci soient supprimés.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur POP3](../core/configuring-the-pop3-adapter.md)