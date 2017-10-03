---
title: "Générer un client WCF ou un contrat de service WCF pour les artefacts de solution Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, generate a client class by using svcutil.exe
- creating a proxy
- how to, create a proxy
- WCF service model, creating a proxy
- how to, generate a client class by using the Add Adapter Service Reference Plug-in
- how to, generate a client class
ms.assetid: 52c32c86-6403-4bb4-9d43-1319d19a6b49
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c75615f0e6a3f6e4c947a7c13888558b7a666e77
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts"></a>Générer un client WCF ou un contrat de service WCF pour les artefacts de solution Siebel
Vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ciblé sur les opérations sélectionnées sur les artefacts Siebel. Vous pouvez également utiliser le service Model Metadata Utility Tool (svcutil.exe) pour générer la classe de client WCF ; Toutefois, le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] expose les fonctionnalités de l’utilitaire de métadonnées ServiceModel via une interface de Microsoft Windows standard. Il fournit également des fonctionnalités de navigation et de recherche qui ne sont pas disponibles avec l’outil svcutil.exe et génère un fichier de configuration basé sur les propriétés de liaison que vous sélectionnez lorsque vous vous connectez au système Siebel.  
  
## <a name="generating-a-wcf-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>Génération d’une classe de Client WCF à l’aide de l’ajouter une référence de Service d’adaptateur plug-in  
 Procédez comme suit pour générer une classe de client WCF à l’aide de la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### <a name="to-generate-a-wcf-client-class"></a>Pour générer une classe de client WCF  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur votre projet, puis cliquez sur **ajouter une référence de Service de carte**.  
  
2.  Après le **ajouter une référence de Service de carte** boîte de dialogue s’ouvre, suivez les étapes de [récupérer des métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md) pour se connecter au système Siebel et Parcourir, rechercher opérations. Pour créer une classe de client WCF pour les opérations que vous sélectionnez, assurez-vous que **Client (Outbound operations)** est sélectionné dans le **type de contrat Select** liste déroulante (il s’agit de la valeur par défaut).  
  
3.  Après avoir sélectionné toutes les opérations que vous souhaitez cibler, cliquez sur **OK** pour générer la classe de client WCF.  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ajoute deux fichiers à votre projet :  
  
-   Le fichier de code du client WCF. Ce fichier contient le WCF client classe et assistance code généré pour les opérations que vous avez sélectionné. La première fois que vous exécutez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] il génère ce fichier avec le nom par défaut **SiebelBindingClient.cs** . Si vous l’exécutez à nouveau, le fichier suivant, il génère sera appelé **SiebelBindingClient1.cs**.  Le suffixe du numéro augmente de 1 pour chaque nouveau fichier que vous générez.  Vous pouvez également modifier le préfixe par défaut **SiebelBinding** en entrant un préfixe différent dans le **préfixe de nom de fichier** champ le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] avant de sélectionner **OK** à générer le fichier.  
  
-   **App.config**. Ce fichier contient une configuration de liaison et les configurations de point de terminaison client qui sont basées sur les sélections effectuées lors de la configuration de la connexion pour le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour plus d’informations sur le contenu du fichier app.config, consultez [configurer un Client WCF pour un système Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).  
  
    > [!IMPORTANT]
    >  Lors de l’utilisation du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier app.config. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier app.config, si nécessaire.  
  
## <a name="generating-a-wcf-client-class-by-using-svcutilexe"></a>Génération d’une classe de Client WCF à l’aide de svcutil.exe  
 Vous pouvez utiliser svcutil.exe pour générer une classe de client WCF pour votre application. Vous devez configurer svcutil.exe pour l’utiliser avec le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]. Pour plus d’informations sur la configuration et l’utilisation de svcutil.exe avec la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [à l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md).  
  
 SvcUtil.exe génère la classe de client WCF dans un fichier de sortie avec un nom de fichier par défaut de output.cs. Vous devez inclure manuellement ce fichier dans votre [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des Applications Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)