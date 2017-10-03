---
title: "Création de Ports | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, creating
- receive ports
- creating, send ports
- creating, ports
- Configuration database [BizTalk Server], connecting
- receive ports, creating
- send ports
- send ports, creating
ms.assetid: 4f99f884-5b84-4f9f-8cec-dd5da259ba7f
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdb7ff7d93b754285e9ed0eb627ca24b113bd2a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-ports"></a>Création de ports
Les procédures suivantes permettent de créer des ports d'envoi et de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'authentification unique.  
  
## <a name="creating-a-send-port"></a>Création d'un port d'envoi  
  
#### <a name="to-create-a-send-port"></a>Pour créer un port d’envoi  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    1.  Tapez un nom pour le port d’envoi, par exemple, `SSOSendToPeopleSoft`.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **PeopleSoft**.  
  
    3.  À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.  
  
    4.  Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
    6.  Cliquez sur **configurer** pour configurer le port d’envoi.  
  
4.  Dans le **propriétés du Transport PeopleSoft** boîte de dialogue zone, procédez comme suit :  
  
    1.  Développez **propriétés obligatoires de l’adaptateur**, puis entrez **chemin d’accès au serveur d’Application**, **JAVA_HOME**, **nom d’utilisateur**,  **mot de passe**et le fichier Jar pour la connexion au système Peoplesoft.  
  
         Il n'est pas nécessaire de définir les informations de connexion.  
  
    2.  Dans la liste, sélectionnez l'application associée SSO que vous avez créée pour représenter le système PeopleSoft.  
  
    3.  Pour **utiliser SSO**, sélectionnez **Oui**.  
  
    4.  Cliquez sur **OK**.  
  
5.  Cliquez sur **OK**.  
  
## <a name="creating-a-receive-port"></a>Création d'un port de réception  
  
#### <a name="to-create-a-receive-port"></a>Pour créer un port de réception  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.  
  
2.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Ports de réception unidirectionnels**.  
  
3.  Dans le **propriétés du Port de réception** fenêtre, dans le **général** page, procédez comme suit :  
  
    1.  Dans le **nom** , tapez `ReceiveFromTIBCOEMS`.  
  
    2.  Dans le **authentification** zone de groupe, spécifiez le traitement des messages lors de l’utilisation de l’authentification.  
  
    3.  Sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher.  
  
4.  Sur le **emplacements de réception** page, procédez comme suit :  
  
    1.  Cliquez sur **Nouveau**.  
  
    2.  Dans le **emplacements de réception** fenêtre, dans le **général** , tapez le **nom** l’emplacement de réception.  
  
    3.  À partir de la **Type** liste déroulante, sélectionnez le type de transport et à partir de la **Gestionnaire de réception** liste déroulante, sélectionnez l’adresse de transport.  
  
    4.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline de réception.  
  
    5.  Sur le **planification** page, sélectionnez le **date de début** et **date de fin** pour restreindre la réception des documents.  
  
    6.  Sélectionnez le **activer la fenêtre de service** case à cocher.  
  
    7.  Cliquez sur **OK**.  
  
5.  Sur le **mappages entrants** , sélectionnez les mappages entrants pour transformer les documents sur le port sélectionné.  
  
6.  Sur le **suivi** , sélectionnez le suivi des propriétés de message et le suivi des corps de message souhaité.  
  
7.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-single-sign-on2.md)