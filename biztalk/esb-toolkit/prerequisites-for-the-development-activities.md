---
title: "Conditions préalables pour les activités de développement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54c91405-f9a4-4676-b5c5-fe90b3b51b45
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efdb0a358b378886b8944c9d3d9428b169bab7a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prerequisites-for-the-development-activities"></a>Conditions préalables pour les activités de développement
Cette section décrit comment préparer votre environnement pour effectuer les étapes décrites dans les activités de développement qui sont incluses dans le cadre de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. Terminer la configuration suivante avant de tenter d’une des procédures dans les activités de développement :  
  
## <a name="set-up-your-computer-to-perform-the-procedures-in-the-biztalk-esb-toolkit-development-activities"></a>Configurer votre ordinateur pour effectuer les procédures décrites dans les activités de développement de BizTalk ESB Toolkit  
  
1.  Installer et déployer l’application d’exemple de feuille de route, l’exemple d’application de résolution dynamique et l’exemple d’application de plusieurs Services Web. Pour plus d’informations sur l’installation et le déploiement de ces applications, consultez [exemples d’Applications BizTalk ESB Toolkit](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md).  
  
2.  Exécutez l’utilitaire de serveur de publication UDDI.  
  
3.  Sur votre ordinateur de développement, dans l’Explorateur Windows, créez les chemins d’accès suivants :  
  
    -   C:\HowTos  
  
    -   C:\HowTos\Itineraries  
  
    -   C:\HowTos\DropFolder  
  
    -   C:\HowTos\Out  
  
4.  Vérifiez que votre [!INCLUDE[prague](../includes/prague-md.md)] compte de service a **contrôle total** des autorisations pour la structure de répertoires C:\HowTos.  
  
5.  Assurez-vous que votre compte de service Microsoft BizTalk Server a **écrire** autorisations pour C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out.  
  
6.  Dans le dossier C:\HowTos, copiez le message de test suivant :  
  
    -   C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Test\Data\NAOrderDoc.Xml  
  
7.  Dans le dossier C:\HowTos, créez un raccourci vers l’application Client de Test d’itinéraire, à l’emplacement suivant :  
  
    -   C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Source\ESB. Itinerary.Test\bin\Debug\ESB. Itinerary.Test.exe  
  
## <a name="create-the-visual-studio-solution"></a>Créer la solution Visual Studio  
  
1.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], dans le menu fichier, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, dans le volet types de projet, cliquez sur **Visual C#**, puis cliquez sur **bibliothèque de classes** dans le volet Modèles.  
  
3.  Dans le **nom** , tapez **ItineraryLibrary**.  
  
4.  Dans le **emplacement** , tapez **C:\HowTos**.  
  
5.  Sélectionnez le **créer le répertoire pour la solution** case à cocher.  
  
6.  Dans le **nom de la Solution** , tapez **modèles**, puis cliquez sur **OK** pour créer la solution.  
  
7.  Supprimer le **Class1.cs** de fichiers à partir de la **ItineraryLibrary** projet.