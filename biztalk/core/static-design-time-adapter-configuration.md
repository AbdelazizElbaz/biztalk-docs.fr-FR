---
title: "Configuration de l’adaptateur de conception statique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 332723a4-e39d-43f5-af4d-bf9f56496535
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8337e4f53afe22ccbde0e1d1d2a6437d280011d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="static-design-time-adapter-configuration"></a>Configuration de l'adaptateur de conception statique
La partie conception de l'adaptateur sert à définir toutes les propriétés disponibles et à valider les saisies de l'utilisateur. Dans une configuration de conception statique, l'adaptateur utilise l'interface utilisateur par défaut pour l'affichage et la modification de ses propriétés.  
  
 Cette section explique comment implémenter la fonction de configuration de conception statique pour votre adaptateur personnalisé. Les modifications que vous apporterez seront fonction des besoins des applications avec lesquelles communique l'adaptateur et de la logique mise en œuvre par l'adaptateur. Des liens vous renvoyant vers les sections de l'Aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous sont fournis le cas échéant pour vous guider dans cette procédure. Les endroits de la documentation relative à l'adaptateur File contenant des exemples pertinents vous sont également signalés.  
  
## <a name="guidelines-for-the-static-development-process"></a>Instructions sur le processus de développement statique  
 La liste suivante fournit des recommandations pour la création de la fonction de conception statique pour votre adaptateur. Vous n'êtes pas obligé de suivre toutes les étapes du développement, ni même de respecter l'ordre indiqué.  
  
1.  Créez la liste des conditions requises pour la configuration de l'adaptateur et des paramètres de configuration à définir. Si les paramètres sont utilisés de manière globale par tous les ports d'envoi et emplacements de réception, indiquez-les dans le fichier de configuration du schéma du gestionnaire. S'ils doivent être propres à un port ou à un emplacement, configurez-les dans les fichiers de configuration du port d'envoi et de l'emplacement de réception concernés.  
  
2.  Modifiez les pages de propriétés de l'adaptateur de sorte à tenir compte des nouveaux paramètres de configuration. Pour plus d’informations sur cette étape, consultez [les schémas de Configuration de carte](../core/adapter-configuration-schemas.md).  
  
3.  Modifiez la vue de l'arborescence des catégories de schémas à l'aide de l'Assistant Ajouter les métadonnées de l'adaptateur. Pour plus d’informations sur cette étape, consultez [catégories de schémas dans l’Assistant Ajout de métadonnées d’adaptateur](../core/schema-categories-in-the-add-adapter-metadata-wizard.md)  
  
4.  Modifiez l'exemple de code afin de retourner les schémas sous forme de fichiers WSDL (Web Services Description Language). Pour plus d’informations sur cette étape, consultez [IStaticAdapterConfig Interface de l’adaptateur statique](../core/static-adapter-istaticadapterconfig-interface.md).  
  
5.  Modifiez les fichiers WSDL existants ou créez-en de nouveaux. Pour plus d’informations sur cette étape, consultez [fichiers WSDL de l’adaptateur](../core/adapter-wsdl-files.md).  
  
6.  Modifiez l'exemple de code pour retourner les fichiers XSD supplémentaires requis par l'adaptateur et qui ne figurent pas dans les fichiers WSDL. Pour plus d’informations sur cette étape, consultez [méthode GetSchema de l’adaptateur](../core/adapter-getschema-method.md).  
  
7.  Modifiez les clés de registre de l'adaptateur et exécutez le fichier de registre. Pour plus d’informations sur cette étape, consultez [fichier d’inscription de carte](../core/adapter-registration-file.md).  
  
8.  Installez l'adaptateur statique dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur cette étape, consultez [installer l’adaptateur dans BizTalk Server](../core/install-the-adapter-into-biztalk-server.md).  
  
9. Testez les modifications apportées aux pages de propriétés de l'adaptateur. Recréez l'adaptateur pour tester l'interface utilisateur qui s'affiche dans l'Assistant Ajouter les métadonnées de l'adaptateur. Pour plus d’informations sur cette étape, consultez [générer et tester le projet d’adaptateur](../core/build-and-test-the-adapter-project.md)  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Interface IStaticAdapterConfig de l’adaptateur statique](../core/static-adapter-istaticadapterconfig-interface.md)  
  
-   [Catégories de schémas dans l’Assistant Ajout d’adaptateur métadonnées](../core/schema-categories-in-the-add-adapter-metadata-wizard.md)