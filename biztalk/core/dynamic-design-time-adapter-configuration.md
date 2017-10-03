---
title: "Configuration de l’adaptateur de conception dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36127d62-0348-42bb-981f-19fcad26efce
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de12e705c725c4b8e72cf4b6ffbd4cdf1d939265
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-design-time-adapter-configuration"></a>Configuration de l'adaptateur de conception dynamique
Il peut arriver que la configuration de l'adaptateur de conception statique et l'interface utilisateur par défaut standard de l'Assistant Ajouter les métadonnées de l'adaptateur manquent de flexibilité pour permettre l'affichage des services d'un adaptateur pour un projet BizTalk à importer. Pour remédier à cette situation, vous pouvez utiliser la configuration de conception dynamique et fournir une interface utilisateur personnalisée à l'Assistant dans laquelle afficher et sélectionner les services de l'adaptateur. L'infrastructure d'adaptateurs BizTalk contient un ensemble d'API dont vous pouvez vous servir pour importer les schémas requis pour l'adaptateur et afficher l'interface utilisateur personnalisée.  
  
 Cette section explique comment implémenter la fonction de configuration de conception dynamique pour votre adaptateur personnalisé. Les modifications que vous apporterez seront fonction des besoins des applications avec lesquelles communique l'adaptateur et de la logique mise en œuvre par l'adaptateur. Des liens vous renvoyant vers les sections de l'Aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous sont fournis le cas échéant pour vous guider dans cette procédure. Les endroits de la documentation relative à l'adaptateur File contenant des exemples pertinents vous sont également signalés.  
  
## <a name="guidelines-for-the-dynamic-development-process"></a>Instructions sur le processus de développement dynamique  
 La liste suivante fournit des recommandations pour la création de la fonction de conception dynamique pour votre adaptateur. Pendant le développement peut inutile d’effectuer toutes ces étapes ni de les exécuter dans une séquence rigide.  
  
1.  Créez la liste des conditions requises pour la configuration de l'adaptateur et des paramètres de configuration à définir. Si les paramètres sont utilisés de manière globale par tous les ports d'envoi et emplacements de réception, indiquez-les dans le fichier de configuration du schéma du gestionnaire. S'ils doivent être propres à un port ou à un emplacement, configurez-les dans les fichiers de configuration du port d'envoi et de l'emplacement de réception concernés.  
  
2.  Modifiez les pages de propriétés de l'adaptateur de sorte à tenir compte des nouveaux paramètres de configuration. Pour plus d’informations sur cette étape, consultez [les schémas de Configuration de carte](../core/adapter-configuration-schemas.md).  
  
3.  Créez une interface utilisateur personnalisée dans laquelle l'Assistant Ajouter les métadonnées de l'adaptateur pourra sélectionner le schéma à ajouter au projet. De toutes les recommandations listées ici, seule celle-ci distingue un adaptateur dynamique d'un adaptateur statique. Pour plus d’informations sur cette étape, consultez [méthode DisplayUI de l’adaptateur dynamique](../core/dynamic-adapter-displayui-method.md) et la classe [Microsoft.BizTalk.Adapter.Framework.IDynamicAdapterConfig.DisplayUI](http://msdn.microsoft.com/library/microsoft.biztalk.adapter.framework.idynamicadapterconfig.displayui.aspx).  
  
4.  Modifiez l'exemple de code afin de retourner les schémas sous forme de fichiers WSDL (Web Services Description Language). Pour plus d’informations sur cette étape, consultez [IStaticAdapterConfig Interface de l’adaptateur statique](../core/static-adapter-istaticadapterconfig-interface.md).  
  
5.  Modifiez les fichiers WSDL existants ou créez-en de nouveaux. Pour plus d’informations sur cette étape, consultez [fichiers WSDL de l’adaptateur](../core/adapter-wsdl-files.md).  
  
6.  Modifiez l'exemple de code pour retourner les fichiers XSD supplémentaires requis par l'adaptateur et qui ne figurent pas dans les fichiers WSDL. Pour plus d’informations sur cette étape, consultez [méthode GetSchema de l’adaptateur](../core/adapter-getschema-method.md).  
  
7.  Modifiez les clés de registre de l'adaptateur et exécutez le fichier de registre. Pour plus d’informations sur cette étape, consultez [fichier d’inscription de carte](../core/adapter-registration-file.md).  
  
8.  Installez l'adaptateur statique dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur cette étape, consultez [installer l’adaptateur dans BizTalk Server](../core/install-the-adapter-into-biztalk-server.md).  
  
9. Testez les modifications apportées aux pages de propriétés de l'adaptateur. Recréez l'adaptateur pour tester l'interface utilisateur qui s'affiche dans l'Assistant Ajouter les métadonnées de l'adaptateur. Pour plus d’informations sur cette étape, consultez [générer et tester le projet d’adaptateur](../core/build-and-test-the-adapter-project.md)  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Méthode DisplayUI de l’adaptateur dynamique](../core/dynamic-adapter-displayui-method.md)