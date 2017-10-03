---
title: "Le traitement d’un Message AS2 entrant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 998ff334-71e2-4686-b2b7-44940a0ebed1
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b221ea3697180c27e347250570b0e96105a50f08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-an-incoming-as2-message"></a>Traitement d'un message AS2 entrant
Les pipelines de réception AS2 traitent un message entrant sur AS2. Le pipeline de réception AS2EdiReceive traite un message EDI à l'aide du Désassembleur EDI. Le pipeline de réception AS2Receive traite un message non EDI à l'aide du Désassembleur AS2. Les deux pipelines traitent la charge du message AS2 et génèrent un MDN de façons différentes ; toutefois, les deux pipelines de réception utilisent le décodeur AS2 pour traiter le message AS2.  
  
 Lorsque le pipeline AS2EdiReceivePipeline traite un message AS2 avec une charge EDI, il termine le traitement AS2 du message reçu avant d'effectuer le traitement EDI. Lorsque le pipeline génère un accusé de réception EDI pour la charge EDI d'un message AS2, il doit renvoyer l'accusé de réception EDI de manière asynchrone, car la connexion est fermée par la réponse AS2.  
  
## <a name="the-receive-port"></a>Le Port de réception  
 Un port de réception HTTP permet de recevoir un message AS2 avec une charge EDI ou non-EDI. Si un MDN doit être renvoyé de manière synchrone, le port de réception doit être un port de réception de requête-réponse bidirectionnel.  
  
 Un MDN peut être renvoyé de façon synchrone ou asynchrone. Cela est déterminé par l’en-tête Disposition-notification-to du message AS2, à moins que le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est sélectionnée dans l’onglet d’accord AS2 unidirectionnel de la  **Propriétés de l’accord** boîte de dialogue. Si la propriété est sélectionnée, la façon dont le MDN est retourné est déterminée par le **exiger le MDN asynchrone** propriété dans le **paramètres MDN de l’expéditeur** page de l’onglet d’accord AS2 unidirectionnel de la  **Propriétés de l’accord** boîte de dialogue. Pour plus d’informations, consultez [les Messages AS2](../core/as2-messages.md) et [Messages MDN](../core/mdn-messages.md).  
  
 Si le MDN est renvoyé de manière synchrone, il l'est via le port d'envoi de l'emplacement de réception bidirectionnel. Ce MDN sert de réponse HTTP, par exemple, un 200OK indique que le message a été reçu.  
  
 Si le MDN est renvoyé en mode asynchrone, un port d'envoi distinct doit être utilisé. Si un port d'envoi dynamique est utilisé, le MDN sera envoyé à l'adresse contenue dans l'en-tête Disposition-notification-to.  
  
> [!NOTE]
>  Le port de réception bidirectionnel utilisé pour recevoir les messages AS2 ne doit pas servir à recevoir les messages MDN. Ceux-ci doivent être reçus sur un port de réception unidirectionnel statique. L'utilisation d'un port de réception de requête/réponse pour un MDN renvoyé de façon asynchrone doit empêcher le renvoi d'un message 200OK en réponse à un MDN entrant, qui provoquerait des tentatives de transmission du MDN inutiles.  
  
## <a name="how-the-as2-receive-pipelines-work"></a>Fonctionnement des pipelines de réception AS2  
 Les pipelines de réception AS2 effectuent le traitement suivant pour le message AS2 entrant :  
  
-   Détermine le tiers expéditeur en faisant correspondre AS2-à partir de la valeur de l’en-tête AS2 du message avec la valeur pour AS2-à partir de la liste dans le **identificateurs** page de l’onglet d’accord AS2 unidirectionnel de la **Propriétésdel’accord** boîte de dialogue. En cas d'échec, il tente de déterminer le tiers expéditeur en faisant correspondre la propriété de contexte AS2-From définie pour le message entrant avec le nom du tiers. Si une correspondance est trouvée et le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est sélectionnée dans l’onglet d’accord AS2 unidirectionnel de la **propriétés de l’accord** boîte de dialogue, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera les propriétés AS2 associées avec l’accord du tiers pour le traitement du message AS2. Si la propriété n'est pas sélectionnée, le pipeline de réception utilise les balises d'en-tête AS2 dans le message entrant. Si aucun accord n'est trouvé, le pipeline abandonne le traitement, suspend le message et génère une exception.  
  
    > [!NOTE]
    >  Le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété vous permet de valider qu’un message entrant a des propriétés de signature, le chiffrement et compression (si ces propriétés sont spécifiées dans le accord dans le **Validation** onglet de l’accord unidirectionnel) et dans le cas contraire, pour suspendre le message et publie une erreur. Vous devez procéder à ces modifications en accord avec le tiers expéditeur. Pour plus d’informations, consultez [configuration des propriétés AS2](../core/configuring-as2-properties.md).  
  
-   Si l'accord du tiers expéditeur est déterminé, mais qu'une erreur se produit lorsque le pipeline de réception tente de traiter le message AS2, le pipeline définit la propriété de contexte MessageDestination du message AS2 sur SuspendQueue. Le pipeline de réception suspend le message dans la MessageBox. Le pipeline de réception définit aussi la propriété de contexte de `EdiIntAS.IsAS2FailedMessage` sur True. Si un MDN est activé en définissant **exiger le MDN** dans les **paramètres MDN de l’expéditeur** page de l’onglet d’accord AS2 unidirectionnel de la **propriétés de l’accord** sera de boîte de dialogue, le pipeline Renvoie le MDN approprié à l’expéditeur. Le pipeline tente toujours de renvoyer un MDN s'il est exigé.  
  
-   Détermine si le message est un doublon, si le **vérifier les messages en double** option est sélectionnée dans le **Validation** page de l’onglet d’accord AS2 unidirectionnel de la **accord Propriétés** boîte de dialogue. Les messages en double sont détectés en faisant correspondre les valeurs AS2-From, AS2-To et Message-ID du message entrant avec les valeurs des messages précédemment reçus. Si toutes les valeurs correspondent, le pipeline de réception définit la valeur de la propriété de contexte `EdiIntAs.IsAS2MessageDuplicate` sur true. Si le **suspendre les messages en double** est également sélectionnée sur la **Validation** page, le message sera interrompu et une erreur consignée.  
  
-   Récupère le nom de fichier, le cas échéant, de chaque pièce jointe et le promeut vers les propriétés de contexte.  
  
-   Effectue une copie du message (au format câble) et la stocke dans la base de données de réception de non répudiation, si activé dans les propriétés de l'accord unidirectionnel AS2.  
  
-   Exécute le traitement MIME, notamment la vérification de la signature et le déchiffrement du message (en fonction des balises d'en-tête).  
  
-   Décompresse le message reçu, s'il était compressé.  
  
-   Génère une réponse HTTP, ajoutée au MDN en mode de réception synchrone de type requête-réponse, ou envoyé en tant que réponse autonome en mode asynchrone.  
  
-   Génère une réponse MDN, si elle est exigée. Le pipeline génère un MDN en fonction des propriétés de l’accord, si le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est définie, ou à partir des propriétés de contexte, si cette propriété n’est pas définie. Si les paramètres de configuration et les en-têtes du message entrant ne sont pas cohérents, le pipeline génère un MDN négatif.  
  
-   Le Désassembleur EDI du pipeline de réception AS2EdiReceive génère un accusé de réception EDI, si le message est EDI et qu'un accusé de réception a été activé. Le pipeline achemine l'accusé de réception EDI vers la base de données MessageBox, à partir de laquelle un port d'envoi dynamique l'enverra de manière asynchrone. Les accusés de réception EDI sont toujours envoyés de façon asynchrone via le transport AS2, parce qu'un MDN ou une réponse HTTP est envoyée de façon synchrone.  
  
-   Effectue une copie du message MDN et la stocke dans la base de données de réception de non répudiation, si activé dans les propriétés de l'accord unidirectionnel AS2.  
  
-   Effectue une copie du message décodé et la stocke dans la base de données de réception de non répudiation, si activé dans les propriétés de l'accord unidirectionnel AS2.  
  
 En cas d'erreur AS2, le message reçu ne subira plus aucun traitement. Toutefois, le pipeline de réception génèrera une réponse MDN.  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md)   
 [Messages AS2](../core/as2-messages.md)   
 [Messages MDN](../core/mdn-messages.md)