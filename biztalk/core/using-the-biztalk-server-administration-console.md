---
title: "À l’aide de la Console Administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Administration Console [BizTalk Server], how to
- Administration Console [BizTalk Server], about Administration Console
- artifacts, list
- groups, Hub
ms.assetid: af00d9de-0f94-407b-b6f4-4da63a0867a0
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de8b806c8a6f39608608a3eabc975cf606410abc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-the-biztalk-server-administration-console"></a>À l’aide de la Console Administration de BizTalk Server
La console Administration de BizTalk Server est une console MMC (Microsoft Management Console) que vous pouvez utiliser pour gérer et surveiller BizTalk Server, mais aussi pour déployer et gérer vos applications BizTalk Server.  
  
 La partie gauche de cette console, appelée arborescence de la console, se compose de dossiers et de sous-dossiers représentant les différents types d'artefacts que vous pouvez gérer.  
  
 Quand vous sélectionnez un nœud dans l'arborescence de la console, le volet des détails qui occupe la partie droite de la console affiche des informations sur les éléments.  
  
 Le nœud Administration de BizTalk Server dans l’arborescence de la console affiche la page de démarrage, qui contient les actions que vous pouvez effectuer, par exemple vous connecter à un groupe BizTalk Server existant. Cette page contient aussi des liens vers la documentation de BizTalk Server et les sites Web de la communauté en ligne.  
  
 Pour plus d’informations sur l’utilisation des raccourcis clavier pour la console d’Administration, consultez [raccourcis clavier la Console Administration](../core/administration-console-keyboard-shortcuts.md).  
  
## <a name="biztalk-server-artifacts"></a>Artefacts de BizTalk Server  
 La console Administration de BizTalk Server permet de gérer les artefacts suivants :  
  
-   **Groupe BizTalk**. le nœud Groupe BizTalk de l'arborescence de la console contient des nœuds supplémentaires qui représentent les artefacts (applications, tiers et paramètres de plateforme) pour ce groupe. Les groupes BizTalk sont des unités d'organisation représentant généralement des entreprises, des services ou d'autres divisions qui nécessitent une implémentation clairement circonscrite de BizTalk Server. Un groupe BizTalk a une relation un-à-un avec une base de données de gestion BizTalk. Pour plus d’informations, consultez [la gestion des groupes](../core/managing-groups.md).  
  
     Lorsque vous sélectionnez le nœud Groupe BizTalk dans la console Administration de BizTalk Server, la page Hub du groupe BizTalk Server s'affiche dans le volet Détails. Cette page fournit une vue d'ensemble du fonctionnement de votre système BizTalk Server. Pour plus d’informations, consultez [à l’aide de la Page Hub du groupe](../core/using-the-group-hub-page.md).  
  
-   **Orchestration**. une orchestration est conçue à l'aide du Concepteur d'orchestration et déployée dans le groupe BizTalk sous lequel elle apparaît dans la console Administration. Pour plus d’informations, consultez [la gestion des Orchestrations](../core/managing-orchestrations.md).  
  
-   **Liens de rôle**. un lien de rôle désigne une relation entre les rôles définis par les types de ports et de messages utilisés lors des interactions dans les deux sens. Pour plus d’informations, consultez [gestion des liens de rôle](../core/managing-role-links.md).  
  
-   **Groupes de ports d’envoi**. un groupe de ports d'envoi est un regroupement nommé de ports d'envoi que vous pouvez utiliser pour envoyer le même message à plusieurs destinations dans le cadre d'une configuration unique. Pour plus d’informations, consultez [gestion des Ports d’envoi et groupes de ports d’envoi](../core/managing-send-ports-and-send-port-groups.md).  
  
-   **Ports d’envoi**. un port d'envoi est un objet BizTalk qui envoie des messages. Pour plus d’informations, consultez [gestion des Ports d’envoi et groupes de ports d’envoi](../core/managing-send-ports-and-send-port-groups.md).  
  
-   **Ports de réception**. un port de réception est un groupe logique d'emplacements de réception similaires. Pour plus d’informations, consultez [Ports de réception gestion](../core/managing-receive-ports.md).  
  
-   **Emplacements de réception**. un emplacement de réception est une adresse spécifique à laquelle parviennent les documents entrants, combinée à un pipeline BizTalk Server qui traite les messages reçus à cette adresse. Pour plus d’informations, consultez [la gestion des emplacements de réception](../core/managing-receive-locations.md).  
  
-   **Stratégies**. une stratégie est une collection avec versions de règles d'entreprise. Pour plus d’informations, consultez [gestion des stratégies de](../core/managing-policies.md).  
  
-   **Schémas**. un schéma est la structure d'un message. Il peut contenir plusieurs sous-schémas. Pour plus d’informations, consultez [la gestion des schémas](../core/managing-schemas.md).  
  
-   **Mappages**. un mappage est un fichier XML qui définit la correspondance entre les enregistrements et les champs d'une spécification et ceux d'une autre spécification. Il comporte une feuille de style XSL utilisée par BizTalk Server pour effectuer la transformation qu'il décrit. Pour plus d’informations, consultez [la gestion des mappages](../core/managing-maps.md).  
  
-   **Pipelines**. un pipeline est une infrastructure logicielle qui définit et relie une ou plusieurs étapes de traitement, puis les exécute dans l'ordre pour réaliser une tâche spécifique. Les pipelines divisent le traitement en étapes, ou abstractions, qui décrivent une catégorie de travail. Ils déterminent également l'ordre dans lequel chaque catégorie de travail est exécutée. Pour plus d’informations, consultez [la gestion des Pipelines](../core/managing-pipelines.md).  
  
-   **Ressources**. une ressource est un script, un assembly déployé ou tout autre fichier associé à une application. Pour plus d’informations, consultez [gestion des ressources](../core/managing-resources.md).  
  
-   **Parties**. Votre organisation peut compter des milliers de partenaires. L'ensemble des partenaires avec lesquels votre société traite sont considérés comme des tiers. Pour plus d’informations, consultez [la gestion des Parties](../core/managing-parties.md).  
  
-   **Paramètres de plateforme**. le nœud Paramètres de plateforme contient des sous-nœuds pour les hôtes, les instances d'hôte, les bases de données MessageBox et les adaptateurs. Pour plus d’informations, consultez [la gestion des paramètres de plateforme](../core/managing-platform-settings.md).  
  
    -   **Hôtes**. le nœud Hôtes contient tous les hôtes isolés et ceux de type In-process de l'environnement BizTalk Server. Un hôte BizTalk est un conteneur logique d'éléments tels que des gestionnaires d'adaptateur, des emplacements de réception (y compris des pipelines) et des orchestrations. Pour plus d’informations, consultez [gestion d’hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md).  
  
    -   **Instances de l’hôte**. le nœud Instances de l'hôte contient toutes les instances de l'hôte du groupe BizTalk Server actuel. Les instances de l'hôte désignent les processus du moteur d'exécution BizTalk Server qui exécutent les composants de votre application.  
  
         Avec le nœud Instances de l'hôte, vous pouvez créer des instances de l'hôte et actualiser les informations sur ces instances. Pour plus d’informations, consultez [gestion d’hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md).  
  
    -   **Serveurs**. le nœud Serveurs répertorie tous les serveurs associés au groupe BizTalk Server. Il s'agit des ordinateurs sur lesquels BizTalk Server est installé et configuré, et sur lesquels les instances d'hôte sont exécutées. Les instances de l'hôte sont créées en associant un serveur à un hôte particulier. Pour plus d’informations, consultez [gestion des serveurs](../core/managing-servers.md).  
  
    -   **Boîtes de message**. le nœud MessageBox contient toutes les bases de données MessageBox utilisées par le groupe BizTalk Server actuel. Avec ce nœud, vous pouvez créer des base de données MessageBox et actualiser les informations sur les bases de données MessageBox. La base de données MessageBox est à la base de l'équilibrage de la charge des opérations entre les serveurs de traitement coopératif. Une opération peut passer plusieurs fois par une base de données MessageBox au cours de son traitement. Le nom de la base de données MessageBox est limité à 100 caractères. Pour plus d’informations, consultez [la gestion des bases de données MessageBox](../core/managing-messagebox-databases.md).  
  
    -   **Adaptateurs**. le nœud Adaptateurs contient les sous-nœuds de tous les adaptateurs d'envoi et de réception configurés pour le groupe BizTalk Server et les gestionnaires d'adaptateur associés. Les adaptateurs constituent le logiciel intermédiaire (middleware) de messagerie utilisé pour envoyer et recevoir des messages entre les points de terminaison. Pour plus d’informations, consultez [à l’aide des adaptateurs](../core/using-adapters.md).  

## <a name="tips-and-tricks"></a>Conseils et astuces

#### <a name="update-settings-for-multiple-hosts-and-host-instances-simultaneously"></a>Mettre à jour simultanément des paramètres pour plusieurs ordinateurs hôtes et les instances d’hôte
En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], vous pouvez sélectionner plusieurs ordinateurs hôtes et les instances d’hôte et mettre à jour certains des paramètres dans **Panneau de configuration**.

**Étapes**:

1. Dans Administration de BizTalk, développez **groupe BizTalk**, développez **paramètres de plateforme**.
2. Sélectionnez **hôtes**. Dans la liste des ordinateurs hôtes, utilisez les touches CTRL ou MAJ pour sélectionner plusieurs ordinateurs hôtes simultanément.
3. Cliquez sur les hôtes que vous avez sélectionné et sélectionnez **paramètres**. Ou bien, sélectionnez **paramètres** dans le volet Actions.
4. Dans le panneau de configuration, général et les paramètres de limitation peuvent être définis et appliqués à plusieurs ordinateurs hôtes que vous avez sélectionné. 
5. Ensuite, sélectionnez **Instances d’hôte**. Dans la liste des instances hôte, utilisez les touches CTRL ou MAJ pour sélectionner plusieurs instances d’hôte simultanément. Dans **paramètres**, le CLR .NET et les paramètres de limitation de l’orchestration peuvent être appliqués à plusieurs instances d’hôte que vous avez sélectionné. 

> [!NOTE]
> Vous pouvez sélectionner plusieurs hôtes et instances d’hôte qui sont du même Type d’hôte. Si le type d’hôte est différent, le **paramètres** option est grisée. Par exemple, si vous hébergez un processus de sélection multiple et un hôte isolé, puis **paramètres** est grisée.

#### <a name="filter-artifacts-in-your-application"></a>Filtrer les artefacts dans votre application
En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], vous pouvez rechercher des artefacts dans votre application. Par exemple, vous pouvez rechercher pour un schéma spécifique ou d’une orchestration dans une application. 

**Étapes**:

1. Dans Administration de BizTalk, développez **groupe BizTalk**, développez **Applications**et développez un de vos applications ayant des artefacts. Par exemple, développez le **Application EDI BizTalk**. 
2. Sélectionnez **schémas**. Dans la liste des schémas, utilisez le **recherche** pour rechercher un schéma, ou filtrer les schémas affichés. Par exemple, tapez **x12** dans la zone de recherche, appuyez sur ENTRÉE. Tous les schémas avec X12 dans le nom sont affichés. Désactivez votre recherche. 

    Ensuite, tapez dans **lot** dans la zone de recherche, appuyez sur ENTRÉE. Les schémas de lot sont affichés. 
    
Vous pouvez utiliser cette recherche pour rechercher ou filtrer les artefacts avec votre application, y compris les ports d’envoi, les ressources, les mappages et ainsi de suite. 

#### <a name="save-multiple-suspended-messages-simultaneously-to-a-file-within-group-hub"></a>Enregistrer les messages suspendus plusieurs simultanément dans un fichier au sein du groupe 
En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], vous pouvez enregistrer plusieurs messages suspendus simultanément dans un fichier.

**Étapes**:

1. Dans Administration de BizTalk, sélectionnez **groupe BizTalk**
2. Sélectionnez **nouvelle requête**et dans la requête, **recherche pour**

    Nom archivé : Recherchez  
    Opérateur : égal à  
    Valeur : Messages
3. Sélectionnez **exécuter la requête**. Dans les résultats de la requête, utilisez les touches CTRL ou MAJ pour sélectionner plusieurs instances suspendues simultanément. Avec le bouton droit, puis sélectionnez **sécurisé au fichier**. 
4. Choisissez le dossier pour enregistrer les fichiers. Une fois enregistré, un fichier XML est créé pour chaque message.

## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment ouvrir la Console Administration de BizTalk Server](../core/how-to-open-the-biztalk-server-administration-console.md)  
  
-   [Configuration du suivi à l’aide de la Console Administration de BizTalk Server](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef)  
  
-   [Utilisation de la page Hub du groupe](../core/using-the-group-hub-page.md)