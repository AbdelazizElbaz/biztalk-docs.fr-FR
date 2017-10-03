---
title: "Qu'est-ce que l'adaptateur POP3 ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- POP3 adapters, availability
- authenticating, POP3 adapters
- POP3 adapters, data duplication
- data duplication
- POP3 adapters, receive adapters
- high availability, POP3 adapters
- POP3 adapters, supported platforms
- POP3 adapters, authenticating
- POP3 adapters, algorithims
- receive adapters, POP3 adapters
ms.assetid: 05e9598b-cdfe-4216-b6bf-1b84f8ddfeae
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 592e0475b607de3f9df528a4bab777aa0fb7635d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-pop3-adapter"></a>Qu'est-ce que l'adaptateur POP3 ?
Cette rubrique décrit l'adaptateur de réception POP3.  
  
## <a name="pop3-receive-adapter"></a>Adaptateur de réception POP3  
 L'adaptateur de réception POP3 permet de déplacer des données d'une boîte aux lettres POP3 vers BizTalk Server.  
  
 Les fonctionnalités principales de l'adaptateur de réception POP3 sont les suivantes :  
  
-   extraction de fichier de la boîte aux lettres du serveur POP3 à la demande ;  
  
-   exécution d'interrogations basées sur une planification configurable ;  
  
-   interrogation de la boîte aux lettres du serveur POP3 et envoi de données directement à BizTalk Server ;  
  
-   spécification de la boîte aux lettres du serveur POP3 comme adresse IP ou nom d'hôte, port, nom d'utilisateur et mot de passe ;  
  
-   possibilité de télécharger des messages de serveurs de messagerie exigeant des connexions SSL ;  
  
-   remise de fichier garantie ;  
  
-   traitement MIME implicite, sans nécessité d'utiliser un décodeur MIME dans un pipeline de réception en cas d'utilisation de l'adaptateur POP3.  
  
## <a name="pop3-adapter-supported-platforms"></a>Plateformes prises en charge par l'adaptateur POP3  
 L'adaptateur POP3 est conçu pour opérer avec tout serveur POP3 conforme aux RFC suivantes :  
  
-   **RFC 1939.** Post Office Protocol Version 3 (voir [http://go.microsoft.com/fwlink/?LinkId=58808](http://go.microsoft.com/fwlink/?LinkId=58808))  
  
-   **RFC 1734.** Commande d’authentification POP3 (consultez [http://go.microsoft.com/fwlink/?LinkId=58809](http://go.microsoft.com/fwlink/?LinkId=58809))  
  
-   **RFC 2045.** Multipurpose Internet Mail Extensions (MIME), partie un : Format du corps de Message Internet (consultez [http://go.microsoft.com/fwlink/?LinkId=58810](http://go.microsoft.com/fwlink/?LinkId=58810))  
  
-   **RFC 2046.** Multipurpose Internet Mail Extensions (MIME), partie deux : Types de médias (consultez [http://go.microsoft.com/fwlink/?LinkId=58811](http://go.microsoft.com/fwlink/?LinkId=58811))  
  
-   **RFC 2047.** MIME (Multipurpose Internet Mail Extensions), partie trois : Extensions d’en-tête de Message pour texte Non-ASCII (consultez [http://go.microsoft.com/fwlink/?LinkId=58812](http://go.microsoft.com/fwlink/?LinkId=58812))  
  
 L'adaptateur POP3 a fait l'objet de tests intensifs avec Microsoft Exchange Server 2003.  
  
## <a name="considerations-for-preventing-data-duplication-when-using-the-pop3-adapter"></a>Considérations relatives au blocage de la duplication de données en cas d'utilisation de l'adaptateur POP3  
 L'adaptateur POP3 n'est pas un adaptateur transactionnel. Il est donc sujet au traitement de plusieurs copies d'un même message, ce qui peut entraîner une duplication de données. Il peut arriver que l'adaptateur POP3 produise des copies en double d'un message dans les scénarios suivants :  
  
-   L'adaptateur POP3 supprime toujours les messages de la boîte aux lettres pour la surveillance de laquelle il est configuré après les avoir soumis à BizTalk pour traitement. Si l'adaptateur POP3 extrait un message d'une boîte aux lettres, le soumet à BizTalk Server pour traitement, puis échoue à le supprimer, ce message est de nouveau soumis à BizTalk Server lors de l'interrogation suivante de la boîte aux lettres par l'adaptateur POP3.  
  
-   Si plusieurs instances de l'adaptateur POP3 dans des instances de l'hôte BizTalk distinctes surveillent simultanément la même boîte aux lettres, alors que le serveur POP3 autorise plusieurs connexions simultanées à ses boîtes aux lettres, l'adaptateur remet parfois des copies en double de certains messages.  
  
## <a name="high-availability-for-the-pop3-adapter"></a>Haute disponibilité pour l'adaptateur POP3  
 Certains serveurs POP3 autorisent plusieurs connexions simultanées à une boîte aux lettres donnée. Si plusieurs instances de l'adaptateur POP3 sont configurées pour extraire des messages d'une boîte aux lettres d'un tel serveur POP3, des données sont dupliquées. Vous devez donc configurer une seule instance de l'adaptateur POP3 pour extraire des messages d'une boîte aux lettres autorisant plusieurs connexions simultanées.  
  
 Pour assurer la tolérance de pannes de l'adaptateur POP3 dans ce scénario, il convient de ne configurer qu'un seul gestionnaire de réception pour s'exécuter sur un hôte BizTalk en cluster. Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  
  
## <a name="authentication-warnings-when-multiple-instances-of-the-pop3-adapter-connect-to-the-same-mailbox"></a>Avertissements d'authentification quand plusieurs instances de l'adaptateur POP3 se connectent à la même boîte aux lettres  
 Vous pouvez configurer BizTalk Server de façon à ce que plusieurs instances de l'adaptateur POP3 extraient des messages d'une même boîte aux lettres. Dans ce cas, il se peut que des avertissements d'authentification soient générés dans le journal des applications de BizTalk Server en raison du mécanisme de verrouillage que certains serveurs POP3 utilisent. Ces avertissements n'ayant aucune incidence sur la fonctionnalité de l'adaptateur POP3, vous pouvez les ignorer dans ce scénario.  
  
## <a name="encrypted-messages-received-by-the-pop3-adapter-that-are-sent-to-the-suspended-queue-may-be-viewable-in-clear-text"></a>Possibilité d'afficher en texte clair des messages chiffrés reçus par l'adaptateur POP3 et envoyés à la file d'attente de messages interrompus  
 Vous pouvez configurer l'adaptateur POP3 pour déchiffrer des messages ayant fait l'objet d'un chiffrement numérique. Cela est effectué en définissant le **appliquer le décodage MIME** propriété **True** pour les emplacements de réception qui utilisent l’adaptateur POP3. Si l’adaptateur POP3 reçoit un message chiffré numériquement et la **appliquer le décodage MIME** pour l’emplacement de réception est définie sur **True** l’adaptateur POP3 tente de déchiffrer le message comme suit :  
  
-   L'adaptateur POP3 recherche un certificat privé correspondant au certificat public utilisé pour chiffrer le message. Ce certificat privé doit se trouver dans le magasin de certificats personnels du serveur exécutant l'instance de l'hôte à laquelle le gestionnaire de réception POP3 est lié.  
  
-   Si l'adaptateur POP3 repère un certificat privé correspondant, il l'utilise pour déchiffrer le message électronique.  
  
-   Le message est déchiffré et conservé dans la MessageBox BizTalk.  
  
 Si un message est interrompu après avoir été déchiffré et conservé dans la MessageBox BizTalk, son contenu est visible en texte clair dans la file d'attente de messages interrompus de BizTalk.  
  
 Pour empêcher l'affichage du texte de messages sécurisés dans la file d'attente de messages interrompus, procédez comme suit :  
  
-   Définir le **appliquer le décodage MIME** propriété **False** pour les emplacements de réception qui utilisent l’adaptateur POP3 et déchiffrer le message dans un pipeline avec le composant de pipeline SMIME.  
  
    > [!NOTE]
    >  Cette approche vous empêche de promouvoir des propriétés de messagerie spécifiques vers le contexte du message.  
  
-   Si vous voulez promouvoir des propriétés de messagerie spécifiques vers le contexte du message tout en veillant à ce que les messages chiffrés restent chiffrés en cas de routage vers la file d'attente de messages interrompus, procédez comme suit :  
  
    -   Cochez l’option **activer le routage pour les messages ayant échoué** sur le port de réception qui héberge les emplacements de réception qui utilisent l’adaptateur POP3.  
  
    -   Créez une orchestration pour vous abonner aux messages confrontés à un échec de remise au port de réception hébergeant les emplacements de réception qui utilisent l'adaptateur POP3.  
  
    -   Configurez l'orchestration avec un port d'envoi qui chiffre le message dans un pipeline à l'aide du composant de pipeline SMIME.  
  
    -   Configurez l'orchestration avec une forme de suspension, afin d'interrompre l'instance d'orchestration et le message.  
  
    -   Créez et déployez l'orchestration, puis liez l'orchestration déployée au port de réception approprié.  
  
## <a name="maximum-message-size-supported-by-the-pop3-adapter"></a>Taille maximale de message prise en charge par l'adaptateur POP3  
 L'adaptateur POP3 a été testé pour la réception de messages d'une taille maximale de 50 Mo.  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateur POP3](../core/pop3-adapter.md)