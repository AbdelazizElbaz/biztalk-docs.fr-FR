---
title: "Créer TIBCO EMS artefacts de réception | Documents Microsoft"
description: "Créer le port de réception et définissez les propriétés de transport à utiliser l’adaptateur TIBCO Enterprise Message Service dans BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1307e3c-0237-4f19-a642-58e694fe95d0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf5810dc012c7aa5dcc2fbdfcecd9d59d066ced7
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="create-tibco-ems-receive-artifacts"></a>Créer TIBCO EMS reçoivent des artefacts

## <a name="overview"></a>Vue d'ensemble
Le récepteur TIBCO Enterprise Message Service est un service de port d'écoute qui enregistre une file d'attente ou une rubrique particulière et reçoit les messages associés. L'adaptateur BizTalk pour TIBCO Enterprise Message Service s'enregistre d'abord auprès de TIBCO Enterprise Message Service en ouvrant une nouvelle session, puis il continue l'interrogation pour recevoir des messages. Cette section décrit la configuration du port de réception pour la connexion à TIBCO Enterprise Message Service et l'utilisation d'un fichier XML dans votre orchestration pour interagir avec TIBCO EMS lors de l'exécution.  

## <a name="create-a-receive-port"></a>Créer un port de réception  
  
1.  Dans la Console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez votre application.  
  
2.  Avec le bouton droit **Ports de réception**, sélectionnez **nouveau**, puis cliquez sur **Ports de réception unidirectionnels**.  
  
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

## <a name="set-the-receive-port-transport-properties"></a>Définir des propriétés de port de la réception
Emplacement de réception pour un système d’exploitation TIBCO Enterprise Message System (EMS) le **URL** et **cible Namespace** au système TIBCO EMS sont les seules valeurs de configuration requises.    
 
1.  Développez le **définition système** et entrez les informations requises pour la connexion au serveur TIBCO EMS.  
  
2.  Développez **gestion des messages** et entrez les informations requises.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |**Sélecteur de message**|Les messages ne sont reçus que si cette chaîne renvoie True avec le message dans la destination.<br /><br /> Permet au port de réception de ne récupérer que les messages qui contiennent des propriétés d'en-tête correspondant à l'expression décrite dans ce champ.<br /><br /> La syntaxe des sélecteurs de message est basée sur un sous-ensemble de la syntaxe d'expression conditionnelle SQL92. Cette syntaxe est décrite en détail dans le guide de l'utilisateur de TIBCO EMS.<br /><br /> Par exemple, si un message contient un nom de propriété d'en-tête NewsType, un port de réception ne peut récupérer que ceux dont le type est Sports ou Éditorial.|  
    |**Nombre de tentatives**|Nombre de tentatives du transport. Valeur par défaut est 0.|  
    |**Intervalle avant nouvelle tentative**|Délai d'attente avant que l'adaptateur fasse une nouvelle tentative. La valeur par défaut est de cinq minutes.|  
  
3.  Développez le **définition de la connexion serveur** et entrez les informations requises.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |**Destination**|Paramètre obligatoire. Définit le nom et le type de la destination. Définit la file d'attente ou la rubrique au format suivant : File d'attente[nom.file.attente] ou Rubrique[nom.rubrique].|  
    |**Numéro de port**|Port sur lequel le serveur TIBCO EMS écoute.|  
    |**Nom de serveur**|Paramètre obligatoire. Nom du système qui héberge le serveur TIBCO EMS.|  
  
4.  Indiquez les informations d'identification à l'aide de l'authentification unique (SSO).  
  
     Vous pouvez utiliser deux méthodes pour accéder au système TIBCO EMS. Vous pouvez utiliser les informations d’identification (paramètres nom et mot de passe d’utilisateur) ou l’authentification unique.  
  
    -   Sélectionnez **Oui** dans **utiliser SSO** à utiliser l’authentification unique.  
  
    -   Sélectionnez une application associée sur la liste.  
  
         Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que TIBCO EMS. L'adaptateur Microsoft BizTalk pour TIBCO EMS utilise les informations d'identification d'un utilisateur d'application. Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée.  
  
         Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications5.md).  
  
5.  Développez **informations d’identification utilisateur** et entrez le **nom d’utilisateur** et **mot de passe** pour accéder au serveur TIBCO EMS.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |`Password`|Le mot de passe qui est utilisé pour communiquer avec un démon TIBCO EMS.<br /><br /> Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour TIBCO EMS communiquer avec un démon TIBCO EMS.|  
    |`User Name`|Nom d’un utilisateur qui est utilisé pour communiquer avec un démon TIBCO EMS.<br /><br /> Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour TIBCO EMS communiquer avec un démon TIBCO EMS.|  
  
6.  Cliquez sur **appliquer**, puis cliquez sur **OK**. 

## <a name="next-steps"></a>Étapes suivantes
[Propriétés de contexte de message TIBCO EMS](../core/message-context-properties-in-biztalk-server.md)