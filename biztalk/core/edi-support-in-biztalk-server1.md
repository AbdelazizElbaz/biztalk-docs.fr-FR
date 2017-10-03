---
title: Prise en charge EDI dans BizTalk Serveur1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cddab7a-99ef-4dbb-bb74-9e3d03df3996
caps.latest.revision: "37"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b5edfa2eccfeac9a4d4192b2189877081ddf25a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-support-in-biztalk-server"></a>Prise en charge d'EDI dans BizTalk Server
Cette rubrique fournit une brève présentation générale du traitement EDI et de la manière dont [!INCLUDE[prague](../includes/prague-md.md)] le prend en charge.  
  
## <a name="introduction-to-edi"></a>Présentation de EDI  
 L'échange de données informatisé (EDI) est l'une des solutions les plus couramment utilisées en matière d'échange électronique des données entre partenaires commerciaux. Cette solution est largement orientée messagerie. Les documents sont implémentés en tant que fichiers plats pouvant inclure des documents informatisés traités par lot. Les échanges traités par lot peuvent inclure plusieurs groupes qui peuvent eux-mêmes inclure plusieurs messages ou documents informatisés.  
  
 EDI est constitué de méthodes d'échange de données spécifiques définies par des corps de normes. X12 (normalisé par ANSI et utilisé principalement en Amérique du Nord) et EDIFACT (normalisé par les Nations-Unies et principalement utilisé hors des États-Unis) sont les principales normes EDI. Elles constituent la base des autres normes (par exemple, HIPAA est dérivée de X12 et KEDIFACT en Corée est dérivée d'EDIFACT). Les normes sont relativement proches en termes de schémas de structure de message et d'accusé de réception, tout en conservant certaines différences.  
  
 Les normes EDI définissent les éléments suivants :  
  
-   les formats, jeux de caractères et éléments de données utilisés dans l'échange de documents ;  
  
-   les enveloppes utilisées dans la transaction EDI ;  
  
-   les accusés de réception nécessaires à la vérification de la remise ;  
  
-   les modalités d'une remise précise et garantie, ainsi que les détection et report automatiques des données corrompues ou incorrectes.  
  
 Si les normes EDI établissent les règles relatives à la structure du document, les partenaires commerciaux doivent s'accorder sur les informations spécifiques transmises et leur utilisation. La conception d'un système EDI connectant deux partenaires commerciaux est déterminée par les impératifs liés aux normes et les éléments sur lesquels les partenaires commerciaux s'accordent. Pour plus d’informations sur la messagerie EDI, consultez [messagerie EDI](../core/edi-messaging.md).  
  
> [!NOTE]
>  Les messages EDI sont distincts de leur transport. Les normes EDI ne définissent pas le transport des messages, de sorte que les messages EDI peuvent être envoyés par différents moyens.  
  
## <a name="how-edi-is-implemented-in-biztalk-server"></a>Implémentation d’EDI dans BizTalk Server  
 [!INCLUDE[prague](../includes/prague-md.md)] comprend des fonctionnalités natives assurant la prise en charge d'EDI. EDI est intégré au produit ; Il n’est pas un complément, comme un adaptateur ou d’un accélérateur.  
  
 **Traitement des échanges**  
  
 La fonction EDI assure le traitement côté réception et côté envoi suivant, dans les pipelines, pour appliquer les règles dictées par les normes EDI.  
  
-   Traitement des messages EDI entrants, y compris validation des échanges et création d'accusés de réception.  
  
-   Génération et envoi des messages EDI sortants, notamment validation des échanges et traitement des ACK reçus, selon la configuration.  
  
 **Traitement par lots**  
  
 Le traitement par lot est assuré par l'orchestration et le pipeline de réception :  
  
-   Si un échange traité par lot reçu doit être fractionné, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] le fractionne en documents informatisés qui le composent, génère un fichier XML pour chaque document informatisé et promeut les propriétés nécessaires à la génération du lot côté envoi.  
  
-   Si un échange par lot reçu doit être conservé, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le lot de manière à conserver les groupes ou documents informatisés que le lot contenait à sa réception.  
  
-   Si un échange par lot reçu est à configurer, les lots reçoivent des groupes et documents informatisés dans un échange sortant.  
  
-   Si plusieurs tiers sont abonnés à un échange traité par lot, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie une copie du lot à chaque tiers.  
  
 **Accords de partenariat commercial**  
  
 Les partenaires commerciaux définissent conjointement l'accord de partenariat commercial, ensemble de propriétés définies dans la console Administration de BizTalk. Ces propriétés de tiers, de ports et d'emplacements d'envoi/de réception déterminent le traitement EDI côté envoi et côté réception. Pour plus d’informations sur les accords de partenariat commercial, consultez [accord de partenariat commercial](../core/trading-partner-agreement.md).  
  
 **État de l’échange**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet la publication de rapports d'état spécifiques à EDI. Ces rapports d'état décrivent complètement le statut d'une transaction d'échange de documents EDI, avec les accusés de réception liés à l'échange.  
  
## <a name="edi-components-in-biztalk-server"></a>Composants d’EDI dans BizTalk Server  
 Les composants Microsoft [!INCLUDE[prague](../includes/prague-md.md)] utilisés pour le traitement EDI sont les suivants :  
  
-   L'application EDI BizTalk contenant les artefacts (y compris les pipelines, les orchestrations et les schémas) nécessaires au traitement des documents EDI.  
  
    > [!NOTE]
    >  Lorsque vous configurez la fonctionnalité EDI dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le programme de configuration crée cette application. Lorsque vous créez une application pour le traitement des échanges EDI, vous devez ajouter une référence à l'application EDI BizTalk à partir de votre application. Pour plus d’informations, consultez [comment ajouter une référence à l’Application EDI de BizTalk Server](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
-   Le pipeline de réception EDI BizTalk (pipeline EdiReceive) analyse les documents EDI, fractionne les lots EDI, convertit les documents EDI au format XML, effectue les validations EDI et XSD, et procède au fractionnement en sous-documents HIPAA X12. Pour plus d’informations, consultez [composants de réception EDI](../core/edi-receive-components.md).  
  
-   Le pipeline d'envoi EDI BizTalk (pipeline EdiSend) convertit les documents XML au format X12 ou EDIFACT, sérialise les documents EDI, et effectue les validations EDI et XSD. Pour plus d’informations, consultez [composants d’envoi EDI](../core/edi-send-components.md).  
  
-   L'interface utilisateur de gestion des partenaires commerciaux (TPM) permet de définir les propriétés du traitement pour les partenaires commerciaux impliqués dans l'échange d'un document EDI et le transport d'un document AS2. Pour plus d’informations, consultez [rôle des accords dans le traitement EDI](../core/the-role-of-agreements-in-edi-processing.md) et **EDI et AS2 UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
-   L'orchestration de traitement par lot traite les échanges EDI par lot et définit les propriétés de contexte pour l'envoi de l'échange traité par lot. L'orchestration de routage gère les instances dans lesquelles les messages correspondent à plusieurs lots en créant autant de copies du message que nécessaire. Pour plus d’informations, consultez [le traitement des lots entrants](../core/processing-incoming-batches.md) et [le traitement par lot les Messages EDI sortants](../core/batching-outgoing-edi-messages.md).  
  
-   L'interface utilisateur du rapport d'état fournit l'état complet des échanges EDI et de leurs accusés de réception corrélés. Pour plus d’informations, consultez [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md).  
  
-   Les outils de conception de Visual Studio permettent de générer et valider une instance, de valider un schéma, et de tester et valider un mappage. Pour plus d’informations, consultez [à l’aide des outils de XML au moment du Design](../core/using-design-time-xml-tools.md).  
  
-   Un référentiel de schéma inclut les schémas X12, EDIFACT, HIPAA X12N 4010A XSD, EANCOM et de contrôle. Pour plus d’informations, consultez [prise en charge des schémas de Document EDI](../core/edi-document-schema-support.md).  
  
-   Un outil de migration (outil de migration de tiers) permet de migrer les données de tiers BizTalk Server 2006 R2 ou BizTalk Server 2009 dans [!INCLUDE[prague](../includes/prague-md.md)]. Pour plus d’informations, consultez [migration des artefacts EDI à partir d’une Version précédente de BizTalk Server](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c).  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement EDI dans BizTalk Server](../core/edi-processing-in-biztalk-server.md)   
 [Prise en charge HIPAA dans BizTalk Server](../core/hipaa-support-in-biztalk-server.md)   
 [Problèmes de prise en charge EDI](../core/edi-support-issues.md)   
 [Architecture de la Solution EDI](../core/edi-solution-architecture.md)   
 [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md)   
 [Développement et la configuration des Solutions EDI BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md)