---
title: Ajouter l’adaptateur BizTalk pour JD Edwards EnterpriseOne | Documents Microsoft
description: Ajouter JD Edwards EnterpriseOne sur l’Administration de BizTalk, créer le port d’envoi, configurez les propriétés de transport et utiliser les pipelines XMLReceive et XMLTransmit lors de l’utilisation de l’adaptateur JD Edwards EnterpriseOne dans BizTalk Server
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baecebcd-c324-40aa-bacf-876f45b6c37f
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46496172a1f436a302e5131f5ff55ede66c2a751
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="configure-jd-edwards-enterpriseone-artifacts-in-biztalk-administration"></a>Configurer les artefacts de JD Edwards EnterpriseOne dans Administration de BizTalk
L'adaptateur Microsoft BizTalk pour J.D.Edwards EnterpriseOne contient les dossiers des gestionnaires de réception et d'envoi. Les dossiers incluent BizTalkServerApplication. L'adaptateur BizTalk pour J.D.Edwards EnterpriseOne peut être créé. Il est exécuté de façon In-process avec BizTalk Server et n'est pas exécuté dans un processus d'hôte isolé.  
  
## <a name="add-the-adapter-to-biztalk-administration"></a>Ajouter l’adaptateur à l’Administration de BizTalk 
  
1.  Ouvrez **Administration de BizTalk Server**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, puis développez **paramètres de plateforme**.  
  
2.  Avec le bouton droit **cartes**, sélectionnez **nouveau**, puis sélectionnez **carte**.  
  
3.  Entrez un nom pour la carte. Par exemple, entrez`JDEEnterpriseOne`.  
  
4.  Sélectionnez **JDEEnterpriseOne** à partir de la **carte** liste, puis sélectionnez **OK**.  

## <a name="create-the-send-port"></a>Pour créer un port d'envoi  
  
1.  Dans **Administration de BizTalk Server**, développez **Applications**, puis développez l’application que vous souhaitez héberger les artefacts
  
2.  Avec le bouton droit **Ports d’envoi**, sélectionnez **nouveau**, puis sélectionnez **Port statique avec sollicitation-réponse**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    -   Dans **nom**, entrez le nom du port d’envoi. Par exemple, entrez `SendToJDE`.  
  
    -   Dans le **Type** la liste déroulante, sélectionnez **JDEdwards**.  
  
    -   Dans le **Gestionnaire d’envoi** liste déroulante, sélectionnez l’adresse du Gestionnaire d’envoi.  
  
5.  Sélectionnez **OK** pour enregistrer vos modifications.

## <a name="configure-the-transport-properties"></a>Configurer les propriétés de transport

Les propriétés de transport de JD Edwards EnterpriseOne sont utilisées au moment de la conception et de l'exécution. Dans **propriétés du Transport**, vous définir les paramètres de connexion et les informations d’identification spécifiques au système du serveur et les objets que vous essayez d’accéder.  
  
 Après avoir défini les paramètres de connexion, vous pouvez explorer les tables, vues et procédures du système JD Edwards EnterpriseOne dans l'Assistant Adaptateur.  
  
 Lorsqu'une connexion est effectuée avec JD Edwards EnterpriseOne, les paramètres sont transmis à l'objet de connexion (Utilisateur, Mot de passe, Environnement). Il renvoie une instance de la fonction commerciale de l'application JD Edwards EnterpriseOne. Les informations d'identification sont définies plus en détail par le nom du serveur d'entreprise/d'applications et le port TCP/IP défini sur lequel écoute [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Les valeurs par défaut du port et du nom du serveur d'entreprise sont configurées dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Elles sont également lues à partir du fichier jdeinterop.ini. En cas d'échec d'ouverture de session, vérifiez avec attention les informations d'identification et les valeurs.  
  
### <a name="enter-the-properties"></a>Entrez les propriétés  
  
1.  Dans l’Administration de BizTalk Server, développez **Applications**, puis développez votre application.  
  
2.  Avec le bouton droit **Ports d’envoi**, sélectionnez **nouveau**, puis sélectionnez **Port d’envoi unidirectionnel statique**.  
  
3.  Dans **propriétés de Port d’envoi**, sélectionnez **nom**et le nom de ce port. Par exemple, entrez `JDEEnterpriseOneSend`.  
  
4.  Sous **général**, dans le **Type de Transport** boîte, sélectionnez **JDE EnterpriseOne** dans la liste déroulante.  
  
5.  Dans le **adresse (URI)** propriété, sélectionnez les points de suspension (**...** ). Le **propriétés du Transport JDE EnterpriseOne** ouvrir : 
  
     ![](../core/media/jdeenterprise-trans.gif "JDEEnterprise_Trans")  
  
6.  Dans le **propriétés du Transport JDE EnterpriseOne**propriétés, développez le **propriétés obligatoires de l’adaptateur**et entrez les informations requises pour la connexion au serveur JD Edwards EnterpriseOne.  Respectez les consignes suivantes pour définir les propriétés de transport :  
  
    |Utilisez cette|Pour ce faire|  
    |--------------|----------------|  
    |**Propriétés obligatoires de l’adaptateur**||  
    |Hôte|Tapez le nom de l'ordinateur du serveur hôte (par exemple :<br /><br /> `actsvr1`)<br /><br /> --or--<br /><br /> Tapez l'adresse IP de l'ordinateur (par exemple,<br /><br /> `123.456.0.789`)|  
    |JAVA_HOME|Tapez le chemin d'accès complet à votre installation JDK (par exemple,<br /><br /> `C:\jdk1sdk1.4.2_07`)|  
    |Environnement JDEdwards|Tapez le nom d’un environnement de JD Edwards EnterpriseOne (par exemple, `DV7333`).<br /><br /> DV7333 correspond à un nom commun d'environnement de développement, PY7333 au nom commun de l'environnement de prototype et PD7333 au nom commun de l'environnement de production.|  
    |Fichiers JAR JDEdwards|Entrez le nom complet du fichier et du chemin d'accès pour chaque fichier JAR :<br /><br /> -   C:\JDEOWJars\Connector.jar<br />-   C:\JDEOWJars\Kernel.jar<br />-Program Files\Microsoft BizTalk Adapters for applications\j.d d’entreprise. Edwards EnterpriseOne(r)\Classes\JDEDynAccess.jar<br /><br /> Chaque fichier JAR doit être séparé par un point-virgule (;) et ne doit comporter aucun espace (par exemple :<br /><br /> `<c:>\Connector.jar;<c:>\Kernel.jar;`)|  
    |Mot de passe|Tapez un mot de passe utilisateur. Si vous n'utilisez pas l'authentification unique (SSO), vous devez alors définir des paramètres d'informations d'identification pour l'adaptateur BizTalk pour JD Edwards EnterpriseOne afin d'accéder au système du serveur. Le mot de passe correspond au nom d'utilisateur et détermine les autorisations qui vous sont octroyées lors de l'accès à la base de données.|  
    |Port|Tapez l’identificateur numérique de l’envoi ou de port de réception (par exemple, `6009`).|  
    |Nom d'utilisateur|Tapez le nom de l’utilisateur, puis cliquez sur **OK**.|  
    |**Propriétés de Source de données d’amorçage\*\***||  
    |Nom de la source de données|Tapez le nom de la source de données. Ce nom est obligatoire pour tous les types de données.|  
    |Propriétaire de la base de données|Tapez le nom du propriétaire de la base de données.|  
    |Nom du serveur de base de données|Tapez le nom du serveur de base de données.|  
    |Port du serveur de base de données|Tapez le numéro d'identification du port du serveur de base de données|  
    |Type de base de données|Tapez un seul caractère pour le type de base de données. Par exemple :<br /><br /> **Je** -iSeries<br /><br /> **O** -Oracle<br /><br /> **S** -SQL Server<br /><br /> **L** -SQL Server OLEDB<br /><br /> **W** - UDB|  
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
  
7.  Sélectionnez **OK** pour accepter toutes les propriétés.  
  
### <a name="bootstrap-data-source-required-properties"></a>Propriétés obligatoires de la source de données du programme d'amorçage  
 La section de démarrage est utilisée dans le cadre de l'authentification unique pour fournir un accès aux tables système. Les informations de source de données de démarrage définissent la source de données dans laquelle réside le mappage de configuration des objets (OCM, Object Configuration Mapping).  
  
 Pour les paramètres de source de données de démarrage, tous les paramètres ne sont pas requis pour toutes les plateformes. Si vous utilisez une base de données, vous devrez peut-être mettre à jour la section [JDBj-JDBC DRIVERS] de **jdeinterop.ini** pour déclarer votre pilote JDBC. La liste suivante identifie les paramètres requis par plateforme :  
  
-   **iSeries**. Nom de la source de données, Type de base de données, Nom du serveur de base de données, Nom de la base de données physique  
  
-   **Oracle**. Nom de la source de données, Type de base de données, Nom de la base de données physique, Propriétaire de la base de données  
  
-   **SQL Server**. Nom de la source de données, Type de base de données, Nom du serveur de base de données, Port du serveur de base de données, Nom de la base de données physique, Propriétaire de la base de données  
  
-   **SQL Server OLEDB**. Nom de la source de données, Type de base de données, Nom du serveur de base de données, Port du serveur de base de données, Nom de la base de données physique, Propriétaire de la base de données  
  
-   **UDB**. Nom de la source de données, Type de base de données, Nom de la base de données physique, Propriétaire de la base de données  
  
### <a name="optimize-configuration"></a>Optimisation de la Configuration  
 Les informations suivantes peuvent vous aider à optimiser la configuration de l'adaptateur BizTalk pour JD Edwards EnterpriseOne.  
  
#### <a name="max-concurrent-calls-parameter"></a>Paramètre Nombre maximal d'appels simultanés  
 Vous pouvez utiliser le paramètre `Max Concurrent Calls` dans les instances où le débit dépasse les capacités de traitement principales. Vous ajoutez le paramètre aux adaptateurs dans le **propriétés de Port d’envoi** page pour activer la protection contre les surcharges de message. La valeur par défaut est -1 : les messages sont illimités.  
  
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie des messages à l'adaptateur de transmission, il reçoit d'abord un lot de l'adaptateur et appelle `TransmitMessage()` sur le lot pour transmettre chaque message. Ensuite, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] appelle `Done()` sur le lot et l'adaptateur commence à transmettre les messages au système principal.  
  
 Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] obtient plusieurs lots avant l'appel de `Done`, la commande `Done` peut ne jamais se produire. En définissant le nombre maximal de messages dans un lot, vous pouvez contrôler les messages transmis au système principal.  
  
 Les modifications apportées au paramètre prennent effet en une minute. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit récupérer les modifications de la configuration de l'adaptateur enregistrée dans la base de données SQL.  
  
#### <a name="refresh-agent"></a>Actualiser l'agent  
 Lorsque vous sélectionnez **Oui** pour le **actualiser l’Agent**, vous forcez le processus runtimeagent.exe et browsingagent.exe à redémarrer automatiquement à la demande.  
  
 Par exemple, vous souhaitez que le processus redémarre automatiquement lors de la perte de la connexion au serveur ou vous ajoutez un élément au serveur et celui-ci ne s'affiche pas pour sélection dans l'Assistant Adaptateur Microsoft.  
  
 Le paramètre Actualiser l'agent est défini dans la fenêtre Propriétés du transport et actualise les agents de navigation et d'exécution. Le processus runtimeagent.exe est actualisé après un délai d'une minute ou lors du prochain appel d'envoi.  
  
> [!NOTE]
>  Le processus browsingagent.exe n'est pas actualisé tant que vous ne terminez pas la session de navigation en cours. Par exemple, vous devez quitter « ajouter les éléments générés … » exploration de session et entrer à nouveau pour actualiser le browsingagent.exe.  
  
#### <a name="single-sign-on"></a>authentification unique (SSO, Single Sign-On)  
 Vous pouvez utiliser deux méthodes pour accéder au système JD Edwards EnterpriseOne. Vous pouvez utiliser les informations d'identification (paramètres de connexion des propriétés de transport) ou l'authentification unique (SSO). Sélectionnez **Oui** dans les **utiliser SSO** champ à utiliser l’authentification unique.  
  
 Pour plus d’informations et des instructions de base sur la configuration de l’authentification unique, consultez [sécurité de l’adaptateur BizTalk pour JD Edwards EnterpriseOne](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md).
  
 Vous devez également sélectionner une application associée dans la liste déroulante. Une application associée qui a été créée par des outils de l'authentification unique de l'entreprise représente une application telle que JD Edwards EnterpriseOne. L'adaptateur BizTalk pour JD Edwards EnterpriseOne utilise les informations d'identification d'un utilisateur de l'application.  
  
 Celles-ci sont extraites de la base de données SSO pour le système de serveur pour une application associée spécifiée. Les informations d'identification sont celles de l'utilisateur (utilisateur de l'application) qui a lancé le projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour plus d’informations sur la création d’une application associée, consultez [création d’Applications associées](../core/creating-affiliate-applications4.md). Vous pouvez également consulter l'aide en ligne de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

## <a name="use-the-xmltransmit-and-xmlreceive-pipelines"></a>Utilisez les pipelines XMLTransmit et XMLReceive

Cette carte requiert que vous sélectionnez **XMLTransmit** et **XMLReceive** pour l’envoi et les pipelines de réception respectivement.  
  
  
1.  Dans l’Administration de BizTalk Server, développez **Applications**, puis développez votre application.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    1.  Tapez un nom pour le port d’envoi, par exemple, `SendToJDEEnterpriseOne`.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **JDE EnterpriseOne**.  
  
    3.  À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.  
  
    4.  Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
4.  Cliquez sur **OK**.  


## <a name="see-also"></a>Voir aussi  
 [Développement d’applications](../core/developing-applications2.md)  
 [Authentification unique et adaptateur BizTalk pour JD Edwards EnterpriseOne](../core/single-sign-on-and-biztalk-adapter-for-jd-edwards-enterpriseone.md)   