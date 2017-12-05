---
title: "À l’aide d’utilitaires BizTalk ESB Toolkit | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2dc05ac-831a-44e1-bd44-e41398552ab1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db4a8ef2def05e0b77d272463d7a79f937623b1a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-biztalk-esb-toolkit-utilities"></a><span data-ttu-id="4d6e3-102">À l’aide d’utilitaires BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="4d6e3-102">Using the BizTalk ESB Toolkit Utilities</span></span>
<span data-ttu-id="4d6e3-103">Cette section décrit les différents utilitaires inclus dans le cadre de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4d6e3-103">This section describes various utilities included as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="4d6e3-104">**Utilitaire d’importation d’itinéraire ESB**</span><span class="sxs-lookup"><span data-stu-id="4d6e3-104">**ESB Itinerary Import Utility**</span></span>  
  
 <span data-ttu-id="4d6e3-105">Cet utilitaire se trouve dans le répertoire \bin de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] et est nommé EsbImportUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-105">This utility is located under the \bin directory of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and is named EsbImportUtil.exe.</span></span> <span data-ttu-id="4d6e3-106">Cet utilitaire peut être utilisé pour publier ou déployer l’itinéraire XML dans la base de données ESBItineraryDB.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-106">This utility can be used to publish or deploy the itinerary XML into the ESBItineraryDB database.</span></span>  
  
 <span data-ttu-id="4d6e3-107">La syntaxe de l’utilitaire est comme suit :</span><span class="sxs-lookup"><span data-stu-id="4d6e3-107">The syntax for the utility is as follows:</span></span>  
  
```  
>EsbImportUtil <Parameter1> <Value> <parameter2> <Value>...  
```  
  
 <span data-ttu-id="4d6e3-108">Il peut accepter divers paramètres sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="4d6e3-108">The various parameters it can accept are the following:</span></span>  
  
 <span data-ttu-id="4d6e3-109">/ ? : \<Présentent les paramètres qui aident à\></span><span class="sxs-lookup"><span data-stu-id="4d6e3-109">/?: \<Show the parameters help\></span></span>  
  
 <span data-ttu-id="4d6e3-110">/ f: \<chemin de fichier xml de feuille de route\></span><span class="sxs-lookup"><span data-stu-id="4d6e3-110">/f: \<Itinerary xml file path\></span></span>  
  
 <span data-ttu-id="4d6e3-111">/ c: \<publié &#124; déployé\></span><span class="sxs-lookup"><span data-stu-id="4d6e3-111">/c: \<published &#124; deployed\></span></span>  
  
 <span data-ttu-id="4d6e3-112">/ n: \<nom de la feuille de route par défaut\></span><span class="sxs-lookup"><span data-stu-id="4d6e3-112">/n: \<Default Itinerary name\></span></span>  
  
 <span data-ttu-id="4d6e3-113">/ v: \<version de feuille de route par défaut (format « major.minor »)\></span><span class="sxs-lookup"><span data-stu-id="4d6e3-113">/v: \<Default Itinerary version (format 'major.minor')\></span></span>  
  
 <span data-ttu-id="4d6e3-114">/o : \<remplacer en mode silencieux\></span><span class="sxs-lookup"><span data-stu-id="4d6e3-114">/o: \<Silent overwrite\></span></span>  
  
 <span data-ttu-id="4d6e3-115">Voici quelques exemples d’utilisation de cet utilitaire.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-115">The following are examples of how to use this utility.</span></span>  
  
 <span data-ttu-id="4d6e3-116">Pour publier la base de données de l’itinéraire :</span><span class="sxs-lookup"><span data-stu-id="4d6e3-116">To publish to the Itinerary database:</span></span>  
  
```  
>EsbImportUtil /f:myitinerary.xml /c:published  
```  
  
 <span data-ttu-id="4d6e3-117">Pour déployer la base de données de l’itinéraire :</span><span class="sxs-lookup"><span data-stu-id="4d6e3-117">To deploy to the Itinerary database:</span></span>  
  
```  
>EsbImportUtil  /f:myitinerary.xml /c:deployed  
```  
  
 <span data-ttu-id="4d6e3-118">**Configuration de l’authentification unique conserver l’utilitaire**</span><span class="sxs-lookup"><span data-stu-id="4d6e3-118">**SSO Configuration Persist Utility**</span></span>  
  
 <span data-ttu-id="4d6e3-119">Cet utilitaire se trouve dans le répertoire \bin de le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] et est nommé Microsoft.Practices.ESB.PersistConfigurationTool.exe.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-119">This utility is located under the \bin directory of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and is named Microsoft.Practices.ESB.PersistConfigurationTool.exe.</span></span> <span data-ttu-id="4d6e3-120">Cet utilitaire peut être utilisé pour rendre persistantes les informations de configuration ESB dans la base de données BizTalk SSO.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-120">This utility can be used to persist the ESB configuration information into the BizTalk SSO database.</span></span> <span data-ttu-id="4d6e3-121">Cela peut également servir à afficher des informations de configuration et de supprimer les informations de configuration à partir de la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-121">This can also be used to view configuration information and remove the configuration information from the SSO database.</span></span>  
  
 <span data-ttu-id="4d6e3-122">La syntaxe de l’utilitaire est comme suit :</span><span class="sxs-lookup"><span data-stu-id="4d6e3-122">The syntax for the utility is as follows:</span></span>  
  
 <span data-ttu-id="4d6e3-123">**Pour ajouter une section de configuration :**</span><span class="sxs-lookup"><span data-stu-id="4d6e3-123">**To add a configuration section:**</span></span>  
  
```  
>Microsoft.Practices.ESB.PersistConfigurationTool  /P /F:app.config /S:SectionName /A:ApplicationName  
```  
  
> [!NOTE]
>  <span data-ttu-id="4d6e3-124">Si /S n’est pas fourni, les sections suivantes seront ajoutées : connectionStrings, esb, esb.resolver et cachingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-124">If /S is not provided, the following sections will be added: connectionStrings, esb, esb.resolver and cachingConfiguration.</span></span>  
  
 <span data-ttu-id="4d6e3-125">**Pour supprimer une section :**</span><span class="sxs-lookup"><span data-stu-id="4d6e3-125">**To remove a section:**</span></span>  
  
```  
>Microsoft.Practices.ESB.PersistConfigurationTool  /R /S:SectionName  
```  
  
 <span data-ttu-id="4d6e3-126">Pour afficher une section existante, utilisez les commutateurs de l’application et de la section avec le commutateur /V.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-126">To view an existing section, use the application and section switches with the /V switch.</span></span>  
  
 <span data-ttu-id="4d6e3-127">Pour définir l’administrateur du nom de groupe, utilisez le commutateur AG:AdminGroupName.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-127">To set the administrator group name, use the AG:AdminGroupName switch.</span></span>  
  
 <span data-ttu-id="4d6e3-128">Pour définir le nom de groupe d’utilisateurs, utilisez le commutateur UG:UserGroupName.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-128">To set the user group name, use the UG:UserGroupName switch.</span></span>