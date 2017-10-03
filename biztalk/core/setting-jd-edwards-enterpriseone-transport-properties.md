---
title: "Définition des propriétés de JD Edwards EnterpriseOne Transport | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Concurrent Calls parameter
- JD Edwards EnterpriseOne adapters, transport properties
- transport properties, configuring [JD Edwards EnterpriseOne adapters]
- adapters [JD Edwards EnterpriseOne adapters], transport properties
- Bootstrap Data Source properties
ms.assetid: 7d258ee6-1cb3-4b88-ac41-49e639833574
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ed3118230f2e4ae48676b297ac444da9c392221
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-jd-edwards-enterpriseone-transport-properties"></a>Définition des propriétés du transport JD Edwards EnterpriseOne.
Les propriétés de transport de JD Edwards EnterpriseOne sont utilisées au moment de la conception et de l'exécution. Dans le **propriétés du Transport** boîte de dialogue, vous définissez les paramètres de connexion et les informations d’identification spécifique sur le système du serveur et les objets que vous essayez d’accéder.  
  
 Après avoir défini les paramètres de connexion, vous pouvez explorer les tables, vues et procédures du système JD Edwards EnterpriseOne dans l'Assistant Adaptateur.  
  
 Lorsqu'une connexion est effectuée avec JD Edwards EnterpriseOne, les paramètres sont transmis à l'objet de connexion (Utilisateur, Mot de passe, Environnement). Il renvoie une instance de la fonction commerciale de l'application JD Edwards EnterpriseOne. Les informations d'identification sont définies plus en détail par le nom du serveur d'entreprise/d'applications et le port TCP/IP défini sur lequel écoute [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Les valeurs par défaut du port et du nom du serveur d'entreprise sont configurées dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Elles sont également lues à partir du fichier jdeinterop.ini. En cas d'échec d'ouverture de session, vérifiez avec attention les informations d'identification et les valeurs.  
  
### <a name="to-specify-transport-properties"></a>Pour spécifier les propriétés de transport  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, cliquez à l’intérieur du **nom** zone, puis tapez un nom pour ce port (par exemple, `JDEEnterpriseOneSend`).  
  
4.  Sous **général**, dans le **Type de Transport** boîte, sélectionnez **JDE EnterpriseOne** dans la liste déroulante.  
  
5.  Dans le **adresse (URI)** propriété, cliquez sur le bouton de sélection (**...** ).  
  
     Le **propriétés du Transport JDE EnterpriseOne** boîte de dialogue s’affiche.  
  
     ![](../core/media/jdeenterprise-trans.gif "JDEEnterprise_Trans")  
  
6.  Dans le **propriétés du Transport JDE EnterpriseOne** boîte de dialogue, développez le **propriétés obligatoires de l’adaptateur**et entrez les informations requises pour la connexion au serveur JD Edwards EnterpriseOne.  
  
     Respectez les consignes suivantes pour définir les propriétés de transport :  
  
    |Utilisez cette|Pour ce faire|  
    |--------------|----------------|  
    |**Propriétés obligatoires de l’adaptateur**||  
    |Hôte|Tapez le nom de l'ordinateur du serveur hôte (par exemple :<br /><br /> `actsvr1`)<br /><br /> --ou--<br /><br /> Tapez l'adresse IP de l'ordinateur (par exemple,<br /><br /> `123.456.0.789`)|  
    |JAVA_HOME|Tapez le chemin d'accès complet à votre installation JDK (par exemple,<br /><br /> `C:\jdk1sdk1.4.2_07`)|  
    |Environnement JDEdwards|Tapez le nom d’un environnement de JD Edwards EnterpriseOne (par exemple, `DV7333`).<br /><br /> DV7333 correspond à un nom commun d'environnement de développement, PY7333 au nom commun de l'environnement de prototype et PD7333 au nom commun de l'environnement de production.|  
    |Fichiers JAR JDEdwards|Entrez le nom complet du fichier et du chemin d'accès pour chaque fichier JAR :<br /><br /> -C:\JDEOWJars\Connector.jar<br />-C:\JDEOWJars\Kernel.jar<br />-Program Files\Microsoft BizTalk Adapters for applications\j.d d’entreprise. Edwards EnterpriseOne(r)\Classes\JDEDynAccess.jar<br /><br /> Chaque fichier JAR doit être séparé par un point-virgule (;) et ne doit comporter aucun espace (par exemple :<br /><br /> `<c:>\Connector.jar;<c:>\Kernel.jar;`)|  
    |Mot de passe|Tapez un mot de passe utilisateur. Si vous n'utilisez pas l'authentification unique (SSO), vous devez alors définir des paramètres d'informations d'identification pour l'adaptateur BizTalk pour JD Edwards EnterpriseOne afin d'accéder au système du serveur. Le mot de passe correspond au nom d'utilisateur et détermine les autorisations qui vous sont octroyées lors de l'accès à la base de données.|  
    |Port|Tapez l’identificateur numérique de l’envoi ou de port de réception (par exemple, `6009`).|  
    |Nom d'utilisateur|Tapez le nom de l’utilisateur, puis cliquez sur **OK**.|  
    |**Propriétés de Source de données d’amorçage\*\***||  
    |Nom de la source de données|Tapez le nom de la source de données. Ce nom est obligatoire pour tous les types de données.|  
    |Propriétaire de la base de données|Tapez le nom du propriétaire de la base de données.|  
    |Nom du serveur de base de données|Tapez le nom du serveur de base de données.|  
    |Port du serveur de base de données|Tapez le numéro d'identification du port du serveur de base de données|  
    |Type de base de données|Tapez un seul caractère pour le type de base de données. Exemple :<br /><br /> **Je** -iSeries<br /><br /> **O** -Oracle<br /><br /> **S** -SQL Server<br /><br /> **L** -SQL Server OLEDB<br /><br /> **W** -UDB|  
    |Nom de la base de données physique|Tapez le nom de la base de données physique. Ce nom est obligatoire pour tous les types de bases de données.|  
    |**Contrôle de l’accès concurrentiel**||  
    |Nombre maximal d'appels simultanés|Tapez une valeur numérique pour le **nombre maximal d’appels simultanés**. Ce nombre représente le nombre maximal d’appels simultanés, par exemple, `10`.<br /><br /> La valeur par défaut de ce champ est 5.|  
    |**Actualiser l’Agent**||  
    |Actualiser l'agent|Sélectionnez **Oui** pour le **actualiser l’Agent** pour forcer le processus runtimeagent.exe et browsingagent.exe à redémarrer automatiquement à la demande.<br /><br /> Par exemple, si vous souhaitez que le processus redémarre automatiquement lors de la perte de la connexion au serveur ou si vous ajoutez un élément au serveur et que celui-ci ne s'affiche pas pour sélection dans l'Assistant Adaptateur Microsoft.|  
    |**Serveur de sécurité**||  
    |Nom du serveur de sécurité|Tapez le nom du serveur d'administration de la sécurité. Ce champ est facultatif et il contient par défaut l'hôte du serveur JD Edwards.|  
    |Connexion Nom de service|Tapez le numéro du port utilisé par le serveur d'administration de la sécurité et par le mappage de la configuration de l'objet. La valeur par défaut est le port du serveur JD Edwards.|  
    |**L’authentification unique**||  
    |Application associée|Sélectionnez l'application associée dans la liste déroulante uniquement si vous utilisez l'authentification unique (SSO).|  
    |Utiliser SSO|Sélectionnez **Oui** si vous utilisez l’authentification unique ; un mot de passe n’est pas obligatoire dans ce cas.|  
  
7.  Cliquez sur **OK** pour accepter toutes les propriétés.  
  
## <a name="bootstrap-data-source-required-properties"></a>Propriétés obligatoires de la source de données du programme d'amorçage  
 La section de démarrage est utilisée dans le cadre de l'authentification unique pour fournir un accès aux tables système. Les informations de source de données de démarrage définissent la source de données dans laquelle réside le mappage de configuration des objets (OCM, Object Configuration Mapping).  
  
 Pour les paramètres de source de données de démarrage, tous les paramètres ne sont pas requis pour toutes les plateformes. Si vous utilisez une base de données, vous devrez peut-être mettre à jour la section [JDBj-JDBC DRIVERS] de **jdeinterop.ini** pour déclarer votre pilote JDBC. La liste suivante identifie les paramètres requis par plateforme :  
  
-   **iSeries**. Nom de la source de données, Type de base de données, Nom du serveur de base de données, Nom de la base de données physique  
  
-   **Oracle**. Nom de la source de données, Type de base de données, Nom de la base de données physique, Propriétaire de la base de données  
  
-   **SQL Server**. Nom de la source de données, Type de base de données, Nom du serveur de base de données, Port du serveur de base de données, Nom de la base de données physique, Propriétaire de la base de données  
  
-   **SQL Server OLEDB**. Nom de la source de données, Type de base de données, Nom du serveur de base de données, Port du serveur de base de données, Nom de la base de données physique, Propriétaire de la base de données  
  
-   **UDB**. Nom de la source de données, Type de base de données, Nom de la base de données physique, Propriétaire de la base de données  
  
## <a name="optimization-configuration"></a>Configuration de l'optimisation  
 Les informations suivantes peuvent vous aider à optimiser la configuration de l'adaptateur BizTalk pour JD Edwards EnterpriseOne.  
  
### <a name="max-concurrent-calls-parameter"></a>Paramètre Nombre maximal d'appels simultanés  
 Vous pouvez utiliser le paramètre `Max Concurrent Calls` dans les instances où le débit dépasse les capacités de traitement principales. Vous ajoutez le paramètre aux adaptateurs dans le **propriétés de Port d’envoi** page pour activer la protection contre les surcharges de message. La valeur par défaut est -1 : les messages sont illimités.  
  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie des messages à l'adaptateur de transmission, il reçoit d'abord un lot de l'adaptateur et appelle `TransmitMessage()` sur le lot pour transmettre chaque message. Ensuite, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] appelle `Done()` sur le lot et l'adaptateur commence à transmettre les messages au système principal.  
  
 Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] obtient plusieurs lots avant l'appel de `Done`, la commande `Done` peut ne jamais se produire. En définissant le nombre maximal de messages dans un lot, vous pouvez contrôler les messages transmis au système principal.  
  
 Les modifications apportées au paramètre prennent effet en une minute. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit récupérer les modifications de la configuration de l'adaptateur enregistrée dans la base de données SQL.  
  
### <a name="refresh-agent"></a>Actualiser l'agent  
 Lorsque vous sélectionnez **Oui** pour le **actualiser l’Agent**, vous forcez le processus runtimeagent.exe et browsingagent.exe à redémarrer automatiquement à la demande.  
  
 Par exemple, vous souhaitez que le processus redémarre automatiquement lors de la perte de la connexion au serveur ou vous ajoutez un élément au serveur et celui-ci ne s'affiche pas pour sélection dans l'Assistant Adaptateur Microsoft.  
  
 Le paramètre Actualiser l'agent est défini dans la fenêtre Propriétés du transport et actualise les agents de navigation et d'exécution. Le processus runtimeagent.exe est actualisé après un délai d'une minute ou lors du prochain appel d'envoi.  
  
> [!NOTE]
>  Le processus browsingagent.exe n'est pas actualisé tant que vous ne terminez pas la session de navigation en cours. Par exemple, vous devez quitter « ajouter les éléments générés … » exploration de session et entrer à nouveau pour actualiser le browsingagent.exe.  
  
### <a name="single-sign-on"></a>authentification unique (SSO, Single Sign-On)  
 Vous pouvez utiliser deux méthodes pour accéder au système JD Edwards EnterpriseOne. Vous pouvez utiliser les informations d'identification (paramètres de connexion des propriétés de transport) ou l'authentification unique (SSO). Sélectionnez **Oui** dans les **utiliser SSO** champ à utiliser l’authentification unique.  
  
 Pour plus d’informations et des instructions de base sur la configuration de l’authentification unique, consultez [à l’aide de l’authentification unique sur](../core/using-single-sign-on1.md).  
  
 Vous devez également sélectionner une application associée dans la liste déroulante. Une application associée qui a été créée par des outils de l'authentification unique de l'entreprise représente une application telle que JD Edwards EnterpriseOne. L'adaptateur BizTalk pour JD Edwards EnterpriseOne utilise les informations d'identification d'un utilisateur de l'application.  
  
 Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée. Les informations d'identification sont celles de l'utilisateur (utilisateur de l'application) qui a lancé le projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications4.md). Vous pouvez également consulter l'aide en ligne de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Single Sign-On et adaptateur BizTalk pour JD Edwards EnterpriseOne](../core/single-sign-on-and-biztalk-adapter-for-jd-edwards-enterpriseone.md)   
 [Création de gestionnaires d’envoi de EnterpriseOne JD Edwards](../core/creating-jd-edwards-enterpriseone-send-handlers.md)