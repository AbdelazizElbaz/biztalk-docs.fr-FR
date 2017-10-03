---
title: AS2 Prend en charge dans BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ee230e-8f5f-4b51-99e2-0b38acaf5707
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5e40d7c45ffc8622a420d87bd60e3b74659db93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-support-in-biztalk-server"></a>Prise en charge d'AS2 dans BizTalk Server
Cette rubrique fournit une brève présentation générale du traitement AS2 et de la manière dont [!INCLUDE[prague](../includes/prague-md.md)] l'implémente.  
  
## <a name="introduction-to-as2"></a>Introduction à AS2  
 Les réseaux à valeur ajoutée (RVA) représentent un transport couramment employé dans le cadre du traitement EDI. Il s'agit de réseaux privés qui fournissent des services à valeur ajoutée, tels que des pistes d'audit précises. Toutefois, les sociétés effectuant une migration vers l'échange de documents EDI via Internet, ceci réduit les coûts, augmente la flexibilité et l'efficacité, et offre des avantages en termes de redondance et de fiabilité.  
  
 La méthode d'implémentation EDI sur Internet (EDIINT) la plus répandue est l'utilisation d'AS2 (Applicability Statement 2). La spécification AS2 définit un échange de données d'entreprise MIME pair à pair sécurisé. Les messages contenant une enveloppe avec des données MIME sont transmis à l'aide de HTTP sur TCP/IP.  
  
 AS2 utilise l'opération HTTP POST pour envoyer des données EDI, XML ou d'autres données d'entreprise. L'utilisation d'AS2 n'est pas limitée à l'envoi de données EDI. Request-URI identifie un processus à utiliser pour la décompression et la gestion des données du message. Un MDN (Message Disposition Notification) est renvoyé en tant qu'accusé de réception, soit dans le corps du message de réponse HTTP, soit par une nouvelle opération POST HTTP vers l'URL de l'expéditeur de l'envoi.  
  
 Pour plus d’informations sur la messagerie EDI, consultez [messagerie AS2](../core/as2-messaging.md).  
  
## <a name="how-as2-is-implemented-in-biztalk-server"></a>Implémentation d’AS2 dans BizTalk Server  
 [!INCLUDE[prague](../includes/prague-md.md)] inclut des fonctionnalités natives fournissant une prise en charge d'AS2. Il ne s'agit pas d'un complément au produit, comme un adaptateur ou un accélérateur, mais d'un composant intégré au produit, qui offre les fonctionnalités suivantes :  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise des méthodes AS2 pour envoyer, recevoir et vérifier les messages. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]permet de garantir la sécurité de transfert de données par chiffrement, la signature et la compression. Pour ce faire, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise des clés de chiffrement, des signatures numériques et des certificats.  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'enregistrer les messages AS2 entrants et sortants dans un stockage de non-répudiation. Ceci inclut l'enregistrement des messages AS2 codés ou décodés et des MDN enregistrés.  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de conserver les noms de fichiers des pièces jointes au sein du message AS2.  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de contrôler la présence de messages entrants dupliqués.  
  
-   Vous pouvez renvoyer des MDN de manière synchrone via la connexion du message reçu, ou de manière asynchrone via une autre connexion.  
  
-   Vous pouvez renvoyer un message AS2 si aucun MDN n'est reçu au cours de la période spécifiée.  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet la publication de rapports d'état spécifiques à AS2. Ces rapports fournissent l'état complet d'une transmission AS2, notamment les accusés de réception corrélés à l'échange.  
  
-   AS2 requiert l'utilisation de l'adaptateur HTTP, côté réception et côté envoi.  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de remplacer le certificat de signature par défaut pour les messages AS2 en définissant un certificat par accord. Pour obtenir des instructions sur la façon de spécifier un certificat différent pour un tiers, consultez [configuration des propriétés AS2](../core/configuring-as2-properties.md).  
  
## <a name="as2-components-in-biztalk-server"></a>Composants AS2 dans BizTalk Server  
 Les composants [!INCLUDE[prague](../includes/prague-md.md)] utilisés pour le transport AS2 sont les suivants :  
  
-   L'application EDI BizTalk contenant les artefacts (y compris les pipelines et les schémas) nécessaires au traitement des documents AS2.  
  
    > [!NOTE]
    >  Lorsque vous configurez la fonctionnalité AS2 dans [!INCLUDE[prague](../includes/prague-md.md)], le programme de configuration crée cette application. Lorsque vous créez une application pour le traitement des messages AS2, vous devez ajouter une référence vers l'application EDI BizTalk à partir de votre application. Pour plus d’informations, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
-   Le pipeline AS2EdiReceive qui exécute le traitement AS2, puis le traitement EDI, d'un message EDI reçu via AS2. Pour plus d’informations, consultez [les composants de réception AS2](../core/as2-receive-components.md).  
  
-   Le pipeline AS2Receive, qui exécute le traitement AS2 d'un message non-EDI reçu via AS2. Pour plus d’informations, consultez [les composants de réception AS2](../core/as2-receive-components.md).  
  
-   Le pipeline AS2EdiSend qui exécute le traitement EDI, puis le traitement AS2, d'un message EDI reçu envoyé via AS2. Pour plus d’informations, consultez [composants d’envoi AS2](../core/as2-send-components.md).  
  
-   Le pipeline AS2Send qui exécute le traitement AS2 d'un message non-EDI reçu via AS2. Pour plus d’informations, consultez [composants d’envoi AS2](../core/as2-send-components.md).  
  
-   L'interface utilisateur de gestion des partenaires commerciaux (TPM) qui permet de définir les propriétés du traitement pour les partenaires commerciaux impliqués dans le transport d'un document AS2. Pour plus d’informations, consultez [rôle des accords dans le traitement AS2](../core/the-role-of-agreements-in-as2-processing.md) et **EDI et AS2 UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
-   L'interface utilisateur du rapport d'état qui fournit l'état complet des échanges AS2 et de leurs accusés de réception corrélés. Pour plus d’informations, consultez [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md).  
  
-   L'outil de migration de tiers vous permet de migrer les données de tiers contenant les propriétés AS2 de BizTalk Server 2006 R2 ou BizTalk Server 2009 vers [!INCLUDE[prague](../includes/prague-md.md)]. Pour plus d’informations, consultez [migration des artefacts EDI à partir d’une Version précédente de BizTalk Server](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c).  
  
## <a name="see-also"></a>Voir aussi  
 [AS2 Architecture de la Solution](../core/as2-solution-architecture.md)   
 [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md)   
 [Développement et la configuration des Solutions AS2 BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md)