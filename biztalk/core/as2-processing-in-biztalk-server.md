---
title: AS2 Traitement dans BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0027d3db-24a5-459d-9f4e-a75f49d31d82
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11a5bb12d9a7b21a18b92162370d7be14feda8dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-processing-in-biztalk-server"></a>Traitement AS2 dans BizTalk Server
Cette rubrique offre un aperçu du traitement des messages AS2 côté réception et côté envoi et décrit l'application de la messagerie AS2 grâce aux accords de partenariat commercial.  
  
## <a name="trading-partner-agreements-for-as2-processing"></a>Accords de partenariat commercial pour le traitement AS2  
 Ce type d'accord joue un rôle important dans la prise en charge AS2 dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. La plupart des fonctions de configuration et d'administration liées au traitement AS2 dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont exécutées via la configuration des accords de partenariat commercial entre des profils commerciaux. Les accords combinent les propriétés de traitement des messages bidirectionnelles à partir des profils commerciaux spécifiques des deux partenaires. Les accords reposent sur les paramètres de protocole définis pour chaque profil commercial. Un accord de partenariat commercial entre deux profils commerciaux est appliqué via la définition des propriétés des profils commerciaux impliqués dans l'échange de messages. Les propriétés des profils commerciaux sont définies sous la forme d'un récepteur des messages AS2 et d'un expéditeur des messages AS2 dans l'interface utilisateur de gestion des partenaires commerciaux. Les écrans du module de plateforme sécurisée se trouvent dans le **Parties** nœud de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration. Il n'est pas nécessaire d'être un développeur pour configurer le traitement AS2 dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Vous pouvez définir les propriétés AS2 via les paramètres du protocole de transfert d'un profil commercial ou en spécifiant directement les paramètres AS2 dans l'accord de partenariat commercial. Pour plus d’informations sur les paramètres de protocole, consultez [paramètres de protocole](../core/protocol-settings.md). Pour plus d’informations sur les contrats, consultez [accord de partenariat commercial](../core/trading-partner-agreement.md).  Les fonctionnalités AS2 suivantes sont configurées via la définition des propriétés AS2 spécifiques :  
  
-   Sélectionnez des options de stockage de non-répudiation  
  
-   Spécifiez des propriétés de signature, compression ou chiffrement pour les messages sortants  
  
-   Exigez les MDN pour les messages sortants  
  
-   Définissez les propriétés pour les MDN entrants en remplaçant les propriétés de signature, compression, chiffrement et MDN dans l'en-tête du message AS2.  
  
 Pour plus d’informations sur les accords de partenariat commercial comment dans le traitement AS2, consultez [rôle des accords dans le traitement AS2](../core/the-role-of-agreements-in-as2-processing.md).  
  
> [!NOTE]
>  Contrairement au traitement EDI, il n'y a pas de propriétés globales pour le traitement AS2.  
  
## <a name="as2-receive-side-processing"></a>Traitement AS2 côté réception  
 Les messages AS2 reçus par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont traités via un pipeline de réception AS2. Il existe un pipeline pour recevoir un message EDI sur AS2 (AS2EdiReceive), qui se charge du traitement AS2 et EDI. Un autre pipeline (AS2Receive) ne se charge que du traitement AS2 pour les messages non-EDI reçus sur AS2.  
  
 Le traitement AS2 côté réception inclut les éléments suivants :  
  
-   recherche de l'accord de partenariat commercial ;  
  
    > [!NOTE]
    >  Dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les définitions de tiers incluaient également la définition d'accord. Dans le cadre de la recherche des propriétés d'un tiers, le pipeline de réception effectuait une recherche interne de la définition d'accord au sein de la définition de tiers, puis traitait les messages en conséquence. Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le tiers (ou partenaire commercial) étant distinct de l'accord de partenariat commercial, le pipeline de réception recherche spécifiquement l'accord de partenariat commercial.  
  
    > [!NOTE]
    >  Si tous les accords en fonction desquels un message effectue la résolution sont désactivés, le message sera suspendu.  Un événement est également consigné dans le journal des événements.  
  
-   Enregistrement de copie du message dans la base de données de non-répudiation  
  
-   Vérifier les messages en double  
  
-   traitement des messages contenant plusieurs documents ;  
  
-   récupération du nom de fichier des documents à partir de l'enveloppe MIME ;  
  
-   Déchiffrement du message  
  
-   Décompression du message  
  
-   Vérification de la signature numérique du message  
  
-   Génération d'une réponse HTTP  
  
-   Génération d'une réponse MDN  
  
 Vous devez tenir compte des considérations suivantes dans le cadre de l'utilisation du traitement AS2 côté réception :  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] renvoie une MDN en mode synchrone ou asynchrone. Si le MDN est renvoyé en mode asynchrone, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit utiliser un port d'envoi distinct.  
  
-   Lorsque vous recevez un fichier non-EDI (non XML) sur AS2 et que vous devez effectuer le désassemblage de la charge non-EDI, vous devez utiliser un mécanisme de bouclage avec un second pipeline de réception. Pour plus d’informations, consultez [de traitement côté réception d’un Message Non-EDI entrant via AS2](../core/receive-side-processing-of-an-incoming-non-edi-message-over-as2.md).  
  
-   L'emplacement de réception ne peut utiliser que l'adaptateur HTTP.  
  
-   Pour plus d’informations sur le traitement AS2 côté réception, consultez [comment BizTalk Server reçoit les Messages AS2](../core/how-biztalk-server-receives-as2-messages.md).  
  
-   Pour plus d’informations sur le traitement spécifique effectué par le désassembleur AS2 dans le pipeline de réception, consultez [du traitement d’un Message AS2 entrant](../core/processing-an-incoming-as2-message.md).  
  
## <a name="as2-send-side-processing"></a>Traitement AS2 côté envoi  
 Les messages AS2 sortants générés et envoyés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont traités via un pipeline d'envoi AS2. Il existe un pipeline pour envoyer un message EDI sur AS2 (AS2EdiSend), qui se charge du traitement AS2 et EDI. Un autre pipeline (AS2Send) ne se charge que du traitement AS2 pour les messages non-EDI envoyés sur AS2.  
  
 Le traitement AS2 côté envoi inclut les éléments suivants :  
  
-   recherche de l'accord de partenariat commercial ;  
  
    > [!NOTE]
    >  Dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les définitions de tiers incluaient également la définition d'accord. Dans le cadre de la recherche des propriétés d'un tiers, le pipeline d'envoi effectuait une recherche interne de la définition d'accord au sein de la définition de tiers, puis traitait les messages en conséquence. Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le tiers (ou partenaire commercial) étant distinct de l'accord de partenariat commercial, le pipeline d'envoi recherche spécifiquement l'accord de partenariat commercial.  
  
    > [!NOTE]
    >  Si tous les accords en fonction desquels un message effectue la résolution sont désactivés, le message sera suspendu.  Un événement est également consigné dans le journal des événements.  
  
-   Enregistrement de copie du message dans la base de données de non-répudiation  
  
-   Application d'une enveloppe AS2  
  
-   envoi de plusieurs documents ;  
  
-   stockage du nom de fichier des documents dans l'enveloppe MIME ;  
  
-   Signature du message  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de remplacer le certificat de signature par défaut par un certificat convenu dans l'accord. Pour obtenir des instructions sur la substitution de certificat par défaut pour la signature des messages sortants, consultez [configuration des propriétés AS2](../core/configuring-as2-properties.md).  
  
-   Compression du message  
  
-   Chiffrement du message  
  
-   Calcul d'une valeur MIC pour le MDN  
  
-   traitement d'un MDN entrant (dans le cas d'un MDN synchrone) ;  
  
-   renvoi du message si aucun MDN n'est reçu.  
  
 Vous devez tenir compte des considérations suivantes dans le cadre de l'utilisation du traitement AS2 côté réception :  
  
-   Le port d'envoi ne peut utiliser que l'adaptateur HTTP.  
  
-   Pour plus d’informations sur le traitement AS2 côté envoi, consultez [comment BizTalk Server envoie les Messages AS2](../core/how-biztalk-server-sends-as2-messages.md).  
  
-   Pour plus d’informations sur le traitement spécifique effectué dans le pipeline d’envoi, consultez [génération d’un Message AS2 sortant](../core/generating-an-outgoing-as2-message.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Rôle des accords AS2 de traitement](../core/the-role-of-agreements-in-as2-processing.md)   
 [Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md)   
 [Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md)