---
title: "Composants d’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 383e8bcb-2b4d-40f9-9e98-f49e8d6f30f7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2a5f2a78a9ea555d22f585c0aa50eda65b6c287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-components"></a>Composants d'adaptateur
Un adaptateur personnalisé partage les mêmes méthodes de configuration et de gestion standard que les adaptateurs natifs. Grâce à leur base standard de conception qu'est l'infrastructure d'adaptateurs, il est possible de gérer les adaptateurs personnalisés à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 L’illustration suivante montre les principaux composants d’un adaptateur personnalisé : le fichier de Registre, le composant au moment du design de l’adaptateur et le composant d’exécution de l’adaptateur.  
  
 ![](../core/media/elementsofanadapter.gif "ElementsOfAnAdapter")  
  
## <a name="adapter-registry-file"></a>Fichier de registre de l'adaptateur  
 Certains informations sur les adaptateurs doivent être enregistrées dans le registre et dans la base de données de gestion BizTalk. Les informations telles que l'alias, le gestionnaire de réception, l'emplacement de réception et le type de transport d'un adaptateur sont appelées des métadonnées. Les entrées de ces métadonnées sont créées lors de l'enregistrement manuel de l'adaptateur dans le registre à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez également exécuter l'utilitaire SDK de l'Assistant Registre de l'adaptateur (AdapterRegistryWizard.exe) pour générer le fichier de Registre de votre adaptateur personnalisé. Double-cliquez sur le fichier de Registre ou en cliquant sur **importation** sur la **fichier** menu à l’aide de l’Éditeur du Registre (regedit32.exe) écrit les métadonnées dans le Registre.  
  
> [!NOTE]
>  L'exécution du fichier de registre n'ajoute cependant pas les informations sur l'adaptateur à la base de données de gestion BizTalk. Vous devez procéder vous-même à cette opération dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="design-time-component"></a>Composant de conception  
 L'interface utilisateur d'un adaptateur personnalisé est implémentée à l'aide de l'infrastructure d'adaptateurs. Il s'agit d'une approche intéressante du développement des interfaces utilisateur car l'interface est restituée à partir d'un schéma XML fourni dans le cadre de l'assembly de l'adaptateur. Très peu de code est requis pour transformer le contenu du schéma en interface utilisateur et configurer les propriétés de l'adaptateur.  
  
 Si une orchestration doit communiquer avec un adaptateur d'application tel que l'adaptateur SQL, l'Assistant Ajouter les métadonnées de l'adaptateur vous permet d'ajouter les métadonnées, telles que les schémas, les types de message et les types de port, à un projet BizTalk. Servez-vous de cet Assistant avec les adaptateurs d'applications pour intégrer les schémas correspondants au système. Pour appeler l’Assistant à partir d’un projet BizTalk (non adaptateur), cliquez sur le projet, pointez sur **ajouter les éléments générés**, cliquez sur **ajouter les métadonnées de l’adaptateur** puis sélectionnez dans la liste des enregistrée adaptateurs pour importer les métadonnées de l’adaptateur.  
  
## <a name="run-time-component"></a>Composant d’exécution  
 Un adaptateur se compose généralement de deux composants d’exécution publics : le composant qui implémente le récepteur du message et le composant qui implémente l’expéditeur du message. Leur déploiement peut se faire dans le même assembly ou dans deux assemblys différents.  
  
#### <a name="receive-adapter"></a>Adaptateur de réception  
 L'adaptateur de réception est chargé de créer un message BizTalk en joignant le flux de données réseau/sources au corps du message. Il ajoute également les métadonnées pertinentes au point de terminaison sur lequel les données ont été reçues, puis soumet le message au moteur de messagerie. L'adaptateur supprime les données du point de terminaison de réception ou envoie l'accusé de réception approprié au client, indiquant ainsi que les données ont été acceptées dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
#### <a name="send-adapter"></a>L’adaptateur d’envoi  
 L'adaptateur d'envoi est chargé d'envoyer un message BizTalk au point de terminaison spécifié à l'aide d'un protocole qui lui est spécifique.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelle est l’infrastructure d’adaptateurs ?](../core/what-is-the-adapter-framework.md)