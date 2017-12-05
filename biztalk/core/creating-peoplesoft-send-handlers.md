---
title: "Créer des artefacts d’envoi PeopleSoft adaptateur | Documents Microsoft"
description: "Créer le port d’envoi, envoyer les propriétés de transport et mettre à jour le nombre maximal d’appels simultanés pour envoyer des messages à PeopleSoft à l’aide de l’adaptateur PeopleSoft Enterprise dans BizTalk Server"
ms.custom: 
ms.date: 10/19/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce67da59-26a6-44a2-929c-ed3acb21d407
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bc559f4e3c25560540a171b3f47ff25e6f34e89
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="create-peoplesoft-send-artifacts"></a>Créer des artefacts d’envoi PeopleSoft
L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise accède à PeopleSoft et explore les composants disponibles ou traite les requêtes SOAP. Cette rubrique vous montre comment créer les artefacts de l’envoi d’Administration de BizTalk Server pour utiliser l’adaptateur PeopleSoft.


## <a name="create-the-send-port"></a>Pour créer un port d'envoi

1.  Dans la Console Administration de BizTalk Server, développez **groupe BizTalk**, développez **Applications**, puis développez l’application souhaitée.  
  
2.  Avec le bouton droit **Ports d’envoi**, sélectionnez **nouveau**, puis sélectionnez **Port d’envoi statique avec sollicitation-réponse**.  
  
3.  Dans le **propriétés de Port d’envoi**, procédez comme suit :  
  
    1.  Entrez un nom pour le port d’envoi. Par exemple, entrez `SSOSendToPeopleSoft`.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **PeopleSoft**.  
  
    3.  À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.  
  
    4.  Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
    6.  Sélectionnez **configurer** pour configurer le port d’envoi.  
  
4.  Dans le **propriétés du Transport PeopleSoft**, procédez comme suit :  
  
    1.  Développez **propriétés obligatoires de l’adaptateur**, puis entrez **chemin d’accès au serveur d’Application**, **JAVA_HOME**, **nom d’utilisateur**,  **mot de passe**et le fichier Jar pour la connexion au système Peoplesoft.  
  
         Il n'est pas nécessaire de définir les informations de connexion.  
  
    2.  Dans la liste, sélectionnez l'application associée SSO que vous avez créée pour représenter le système PeopleSoft.  
  
    3.  Pour **utiliser SSO**, sélectionnez **Oui**.  
  
    4.  Sélectionnez **OK**.  
  
5.  Sélectionnez **OK**.

## <a name="set-the-transport-properties"></a>Définir les propriétés de transport
Les propriétés de transport PeopleSoft sont utilisées au moment de la conception et de l'exécution. Dans le **propriétés du Transport** boîte de dialogue, vous définissez les paramètres de connexion et les informations d’identification spécifique sur le système du serveur et les objets que vous essayez d’accéder.  
  
 ![](../core/media/peop-peoplesofttransportpropertiess.gif "Peop_PeopleSoftTransportPropertiess")  
  
1.  Développez les propriétés obligatoires de l'adaptateur et indiquez toutes les informations requises pour la connexion au serveur PeopleSoft.  
  
     Vous devez définir les paramètres de configuration afin de connecter l'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise à PeopleSoft Enterprise. Ces données respectent la casse.  
  
    |Paramètre| Description|  
    |---------------|-----------------|  
    |`Application Server Path`|Chaîne représentant l'ordinateur et le port sur lesquels le serveur d'applications PeopleSoft est exécuté et à l'écoute. La syntaxe du chemin d’accès d’URL pour l’Application PeopleSoft 8 est / / < nom_ordinateur > :\<port\>. Demandez à votre administrateur PeopleSoft pour le \<port\> valeur. Le \<port\> valeur est le JOLT port d’écoute de protocole, pas le port du serveur d’applications. Le port JOLT par défaut est 9000.|  
    |`JAVA_HOME`|Définissez la variable JAVA_HOME pointe vers votre installation JDK, par exemple : **C:\j2sdk1.4.2_08**.|  
    |`Password`|Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour PeopleSoft Enterprise accéder au système de serveur.<br /><br /> Chaîne représentant le mot de passe de l'utilisateur pour la connexion à un système PeopleSoft. Les caractères ne sont pas visibles, mais sont représentés par des astérisques (*).|  
    |`PeopleSoft 8.x Jar Files`|Pour utiliser des interfaces Ccmponent (PeopleSoft 8 uniquement), vous devez mettre à jour le paramètre CLASSPATH de façon à inclure le fichier jar de l'interface de composant pour PeopleSoft. Par exemple : **< PeopleSoft_Home > \web\PSJOA\psjoa.jar**.|  
    |`User Name`|Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour PeopleSoft Enterprise accéder au système de serveur.<br /><br /> Chaîne représentant un nom d'utilisateur requis pour la connexion à un système PeopleSoft.|  
  
2.  Entrez un **des paramètres supplémentaires** de valeur lorsqu’une date est utilisée en tant que clé ; il a un format différent. Le format par défaut est JJ-MM-AAAA.  
  
3.  Entrez un **contrôle d’accès concurrentiel** valeur représentant le nombre d’appels, par exemple 200, dans **nombre maximal d’appels simultanés** si nécessaire.  
  
     Le **nombre maximal d’appels simultanés** paramètre active une protection contre la surcharge si le serveur principal ne peut pas traiter la quantité de données. Un appel simultané est une requête pour laquelle l'adaptateur n'a pas encore de réponse. Définissez **nombre maximal d’appels simultanés** dans les cas où le débit dépasse les capacités de traitement principal.  
  
     La valeur par défaut de ce champ est -1, ce qui correspond à l'absence de protection.  
  
     Si BizTalk Server envoie une demande pour l’adaptateur de transmission et le nombre d’appelle égal à ou dépasse la valeur définie pour **nombre maximal d’appels simultanés**, le thread qui soumet la demande est enregistrée jusqu'à ce que le d’appels simultanés nombre descend en dessous de la valeur définie.  

## <a name="update-max-concurrent-calls"></a>Mettre à jour d’appels simultanés de Max

Le paramètre `Max Concurrent Calls` est une fonctionnalité permettant d'optimiser votre configuration. Vous pouvez utiliser ce paramètre dans les instances où le débit dépasse les capacités du traitement principal. Vous pouvez ajouter le paramètre aux adaptateurs dans le **propriétés de Port d’envoi** boîte de dialogue pour activer la protection contre les surcharges de message. La valeur par défaut est -1 : les messages sont illimités.  
  
Lorsque BizTalk Server envoie des messages à l'adaptateur de transmission, il reçoit tout d'abord un lot de l'adaptateur, puis appelle `TransmitMessage()` sur le lot pour transmettre chaque message. Ensuite, BizTalk Server appelle `Done()` sur le lot et l'adaptateur commence à transmettre les messages au système principal. Si BizTalk Server obtient plusieurs lots avant l'appel de `Done`, la commande `Done` ne peut jamais se produire. En définissant le nombre maximal de messages dans un lot, vous pouvez contrôler les messages transmis au système principal. La modification de ce paramètre entre en vigueur dans une minute. BizTalk Server doit récupérer les modifications de la configuration de l'adaptateur enregistrée dans la base de données SQL.  
  
### <a name="change-the-max-concurrent-calls-parameter"></a>Modifiez le paramètre nombre maximal d’appels simultanés  
  
1.  Dans le **propriétés de Port d’envoi** boîte de dialogue, entrez un **connexion** valeur.  
  
     La valeur par défaut est 40 sessions. Si vous indiquez une valeur inférieure, une dégradation des performances d'exécution peut se produire. L'inverse est également vrai : une valeur supérieure risque de provoquer le dépassement des capacités du serveur et de générer des erreurs d'exécution.  
  
2.  Sélectionnez **Oui** pour **actualiser l’Agent** pour forcer le processus runtimeagent.exe et browsingagent.exe à redémarrer automatiquement à la demande.  
  
     Par exemple, si vous souhaitez que le processus redémarre automatiquement lors de la perte de la connexion au serveur ou si vous ajoutez un élément au serveur et que celui-ci ne s'affiche pas pour sélection dans l'Assistant Adaptateur Microsoft.  
  
     Le **actualiser l’Agent** paramètre actualise les agents de navigation et les moment de l’exécution. Le processus runtimeagent.exe effectue la mise à jour après un délai d'une minute ou à l'appel Envoyer suivant.  
  
3.  Renseignez les informations d'identification pour accéder au système PeopleSoft.  
  
     Deux méthodes permettent d'accéder au système :  
  
    -   les informations d'identification de connexion (paramètres de connexion des propriétés du transport) ;  
  
    -   authentification unique (SSO, Single Sign-On)  
  
4.  Sélectionnez **Oui** pour **utiliser SSO** à utiliser l’authentification unique.  
  
    > [!NOTE]
    >  Pour plus d’informations, consultez [sécuriser l’adaptateur](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md). 
  
5.  Sélectionnez une application associée sur la liste.  
  
     Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que PeopleSoft. L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise utilise les informations d'identification d'un utilisateur d'application. Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée. Les informations d'identification sont celles de l'utilisateur (utilisateur de l'application) qui a lancé le projet BizTalk.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la création d’applications associées, consultez [création d’Applications associées](../core/creating-affiliate-applications2.md), ou l’aide en ligne de Microsoft BizTalk Server.  
  
6.  Après avoir entré toutes les informations requises pour accepter les informations de connexion, cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
     Vous devez définir des paramètres de connexion de l'adaptateur BizTalk pour PeopleSoft Enterprise afin d'accéder à PeopleSoft.  
  

## <a name="next"></a>Suivant
  
[Importer des schémas PeopleSoft dans des projets BizTalk Server](../core/importing-peoplesoft-schemas-into-biztalk-server-projects.md)  
[Recevoir des données de PeopleSoft](../core/receiving-from-peoplesoft.md)