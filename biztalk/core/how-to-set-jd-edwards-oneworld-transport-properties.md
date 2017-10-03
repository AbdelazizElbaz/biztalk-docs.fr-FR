---
title: "Comment définir les propriétés de JD Edwards OneWorld Transport | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setting transport properties
- transport properties, setting
ms.assetid: 6d38088b-a496-414e-aae6-d28c5d6398b6
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7abac3b468b8c76b8214e400366144b39f1e2741
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-jd-edwards-oneworld-transport-properties"></a>Comment définir les propriétés de JD Edwards OneWorld Transport
La définition de système de propriétés du transport JD Edwards OneWorld est utilisée pour la connexion au moment de la conception et de l'exécution. Vous définissez ces informations d'identification pour accéder aux fonctions commerciales de JD Edwards OneWorld au moment de la conception et effectuer des appels au moment de l'exécution.  
  
 Lorsqu'une connexion est établie avec JD Edwards OneWorld, les paramètres sont transmis à l'objet de connexion (utilisateur, mot de passe, environnement). Il renvoie une instance de la fonction d'entreprise de l'application JD Edwards OneWorld. Les informations d'identification sont ensuite définies par le nom du serveur de l'entreprise/application et le port TCP/IP défini sur lequel le service écoute.  
  
 Le nom du serveur de l'entreprise et le port sont lus à partir d'un fichier nommé jdeinterop.ini. Ces valeurs doivent être les mêmes que celles des paramètres Définition de système.  
  
> [!NOTE]
>  Toutes les entrées respectent la casse.  
  
## <a name="setting-properties"></a>Définition de propriétés  
 Dans le **propriétés du Transport** boîte de dialogue, vous définissez les paramètres de connexion et les informations d’identification qui sont spécifiques au système du serveur et les objets que vous essayez d’accéder.  
  
 Les étapes de ce processus sont les suivantes :  
  
#### <a name="to-set-transport-properties"></a>Pour définir les propriétés du transport  
  
1.  Fournissez des informations d'identification.  
  
     Vous pouvez accéder au système JD Edwards OneWorld à l'aide de l'une des méthodes suivantes :  
  
    -   D’informations d’identification (mot de passe, nom d’utilisateur) : Si vous utilisez cette méthode, passez à l’étape 5.  
  
    -   Authentification unique.  
  
2.  Pour utiliser l’authentification unique (SSO), sélectionnez **Oui** dans les **utiliser SSO**.  
  
     Pour plus d’informations sur la façon de configurer l’authentification unique, consultez [à l’aide de l’authentification unique sur](../core/using-single-sign-on3.md).  
  
3.  Sélectionnez une application associée sur la liste.  
  
     Une application associée (créée par les outils d'authentification unique de l'entreprise) représente une application telle que JD Edwards OneWorld. L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld utilise les informations d'identification de l'utilisateur d'une application. Celles-ci sont extraites de la base de données d'informations d'identification SSO pour le système de serveur pour une application associée spécifiée. Les informations d'identification sont celles de l'utilisateur de l'application qui a lancé le projet BizTalk Server.  
  
     Pour plus d’informations, consultez [création d’Applications associées](../core/creating-affiliate-applications3.md).  
  
4.  Développez le **système JD Edwards OneWorld** nœud et entrez les informations requises pour la connexion au serveur JD Edwards OneWorld.  
  
     ![](../core/media/jdedadapter-02-jdesystem.gif "JDEdAdapter_02_JDESystem")  
  
     Après avoir défini les paramètres de connexion, vous pouvez accéder à un système JD Edwards OneWorld. Pour plus d’informations, consultez [l’importation des schémas JD Edwards OneWorld dans des projets de BizTalk Server](../core/importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md).  
  
5.  Entrez une valeur représentant le nombre d’appels, par exemple 200, dans **nombre maximal d’appels simultanés** si nécessaire.  
  
     Le `Max Concurrent Calls` paramètre vous permet d’optimiser votre configuration. Vous utilisez ce paramètre dans des instances où le débit dépasse les capacités du traitement principal pour activer la protection contre la surcharge du message. La valeur par défaut est -1, ce qui signifie que les appels sont illimités.  
  
     Lorsque BizTalk Server envoie des messages à l'adaptateur de transmission, il reçoit tout d'abord un lot de l'adaptateur. Il appelle `TransmitMessage` sur le lot pour transmettre chaque message. Ensuite, BizTalk Server appelle `Done` sur le lot et l'adaptateur commence à transmettre les messages au système principal. Si BizTalk Server obtient plusieurs lots avant l'appel de `Done`, il ne peut jamais se produire. En définissant le nombre maximal de messages dans un lot, vous pouvez contrôler les messages transmis au système principal.  
  
     Les modifications apportées au paramètre prennent effet en une minute. BizTalk Server doit récupérer les modifications de la configuration de l'adaptateur enregistrée dans la base de données SQL.  
  
6.  Sélectionnez **Oui** pour **actualiser l’Agent** pour forcer le processus runtimeagent.exe et browsingagent.exe à redémarrer automatiquement à la demande.  
  
     Par exemple, si vous souhaitez que le processus redémarre automatiquement lors de la perte de la connexion au serveur ou si vous ajoutez un élément au serveur et que celui-ci ne s'affiche pas pour sélection dans l'Assistant Adaptateur Microsoft.  
  
    > [!NOTE]
    >  Le processus browsingagent.exe n'effectue aucune actualisation jusqu'à ce que vous terminiez la session de navigation en cours. Par exemple, vous devez quitter la **ajouter généré un élément** navigation session et pour actualiser le browsingagent.exe.  
  
7.  Après avoir entré toutes les informations requises, cliquez sur **appliquer**, puis cliquez sur **OK** pour accepter les informations de connexion.  
  
     Vous devez définir des paramètres de connexion de l'adaptateur BizTalk pour JD Edwards OneWorld afin d'accéder à JD Edwards OneWorld.  
  
### <a name="adapter-required-properties"></a>Propriétés obligatoires de l'adaptateur  
 Si vous n'avez pas défini de variables d'environnement globales dans le Panneau de configuration, vous pouvez le faire dans cette section.  
  
|Paramètre| Description|  
|---------------|-----------------|  
|`Host`|Tapez le nom du nom d’ordinateur du serveur hôte (par exemple, `actsvr1`) ; ou l’adresse IP de l’ordinateur (par exemple, `123.456.0.789`).|  
|JAVA_HOME|Tapez le chemin d'accès complet à votre installation JDK.|  
|Environnement JDE Edwards|Tapez le nom d’un environnement de JD Edwards OneWorld, par exemple, `DV7333`.<br /><br /> DV7333 correspond à un nom commun d'environnement de développement, PY7333 au nom commun de l'environnement de prototype et PD7333 au nom commun de l'environnement de production.|  
|Fichiers JAR JDEdwards|Entrez le chemin d’accès et le nom complet pour chaque fichier JAR :<br /><br /> -Connector.jar<br />-Kernel.jar<br />-JDEJAccess.jar<br />-JDEActionalInterop.jar<br /><br /> Chaque fichier JAR doit être séparé par un point-virgule (;) et ne doit comporter aucun espace. Exemple :<br /><br /> `<drive>\Connector.jar;<drive>\Kernel.jar;`|  
|Mot de passe|Tapez le mot de passe de l'utilisateur spécifié.|  
|Port|Tapez le numéro de port qui échange des données (par exemple, `6009`).|  
|Nom d'utilisateur|Tapez un nom d'utilisateur JD Edwards OneWorld utilisé pour se connecter au système JD Edwards OneWorld.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires de JD Edwards OneWorld envoi](../core/creating-jd-edwards-oneworld-send-handlers.md)