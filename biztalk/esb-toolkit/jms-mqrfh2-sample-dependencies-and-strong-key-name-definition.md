---
title: "Nom de définition de dépendances JMS MQRFH2 exemple et une clé forte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3a5cdce-dcdf-48df-91a5-8cf2afce9255
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f71915866e807bea8cbd9fdcbf0b1b7ac38a505
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="jms-mqrfh2-sample-dependencies-and-strong-key-name-definition"></a><span data-ttu-id="44b24-102">JMS MQRFH2 exemple dépendances et la définition de nom fort de la clé</span><span class="sxs-lookup"><span data-stu-id="44b24-102">JMS MQRFH2 Sample Dependencies and Strong Key Name Definition</span></span>
<span data-ttu-id="44b24-103">Le projet Visual Studio ESB. JMS. PipelineComponents varie selon le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="44b24-103">The Visual Studio project ESB.JMS.PipelineComponents depends on the following folder:</span></span>  
  
-   <span data-ttu-id="44b24-104">\<Répertoire d’Installation de BizTalk Server >.</span><span class="sxs-lookup"><span data-stu-id="44b24-104">\<BizTalk Server Installation Directory>.</span></span> <span data-ttu-id="44b24-105">Ce dossier permet d’accéder aux espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="44b24-105">This folder provides access to the following namespaces:</span></span>  
  
    -   <span data-ttu-id="44b24-106">**Microsoft::BizTalk::message::Interop**</span><span class="sxs-lookup"><span data-stu-id="44b24-106">**Microsoft::BizTalk::Message::Interop**</span></span>  
  
    -   <span data-ttu-id="44b24-107">**Microsoft::BizTalk::Component::Interop**</span><span class="sxs-lookup"><span data-stu-id="44b24-107">**Microsoft::BizTalk::Component::Interop**</span></span>  
  
## <a name="the-strong-name-key-definition"></a><span data-ttu-id="44b24-108">La définition de clé de nom fort</span><span class="sxs-lookup"><span data-stu-id="44b24-108">The Strong Name Key Definition</span></span>  
 <span data-ttu-id="44b24-109">En règle générale, la définition de clé de nom fort se trouve dans le fichier AssemblyInfo.cpp.</span><span class="sxs-lookup"><span data-stu-id="44b24-109">Usually, the strong-name key definition resides in the AssemblyInfo.cpp file.</span></span> <span data-ttu-id="44b24-110">Toutefois, cela serait en conflit avec le fichier de manifeste C++ qui le compilateur ajoute à l’assembly une fois qu’il lit le fichier AssemblyInfo.cpp.</span><span class="sxs-lookup"><span data-stu-id="44b24-110">However, this would conflict with the C++ manifest file that the compiler adds to the assembly after it reads the AssemblyInfo.cpp file.</span></span> <span data-ttu-id="44b24-111">Ce conflit empêcherait toute tentative visant à placer le fichier dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="44b24-111">This conflict would prevent any attempt to place the file in the global assembly cache.</span></span> <span data-ttu-id="44b24-112">Au lieu de cela, l’éditeur de liens détermine le fichier de clé de nom fort en spécifiant le fichier de clé à... /.. /.. /.. /.. /.. / Keys/Microsoft.Practices.ESB.snk.</span><span class="sxs-lookup"><span data-stu-id="44b24-112">Instead, the linker controls the strong name key file by specifying the key file located at ../../../../../../Keys/Microsoft.Practices.ESB.snk.</span></span> <span data-ttu-id="44b24-113">Pour modifier cette valeur, accédez au paramètre de l’option suivante :</span><span class="sxs-lookup"><span data-stu-id="44b24-113">To edit this value, navigate to the following option setting:</span></span>  
  
 <span data-ttu-id="44b24-114">ESB. JMS. Schémas</span><span class="sxs-lookup"><span data-stu-id="44b24-114">ESB.JMS.Schemas</span></span>  
  
 <span data-ttu-id="44b24-115">Projet \-</span><span class="sxs-lookup"><span data-stu-id="44b24-115">\- Project</span></span>  
  
 <span data-ttu-id="44b24-116">\--Propriétés</span><span class="sxs-lookup"><span data-stu-id="44b24-116">\- - Properties</span></span>  
  
 <span data-ttu-id="44b24-117">\-: Propriétés de configuration</span><span class="sxs-lookup"><span data-stu-id="44b24-117">\- - - Configuration Properties</span></span>  
  
 <span data-ttu-id="44b24-118">\----L’éditeur de liens</span><span class="sxs-lookup"><span data-stu-id="44b24-118">\- - - - Linker</span></span>  
  
 <span data-ttu-id="44b24-119">\-----Avancé</span><span class="sxs-lookup"><span data-stu-id="44b24-119">\- - - - - Advanced</span></span>  
  
 <span data-ttu-id="44b24-120">\------Fichier de clé</span><span class="sxs-lookup"><span data-stu-id="44b24-120">\- - - - - - Key File</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44b24-121">Si vous construisez un composant de Pipeline JMS, vous devez modifier le fichier AssemblyInfo.cpp pour supprimer toutes les références au fichier de clé de nom fort, comme décrit précédemment.</span><span class="sxs-lookup"><span data-stu-id="44b24-121">If you construct a JMS Pipeline Component, you must edit the AssemblyInfo.cpp file to remove any references to the strong-name key file, as described earlier.</span></span> <span data-ttu-id="44b24-122">Après quoi, modifier le **fichier de clé** option dans les propriétés avancées de l’éditeur de liens pour spécifier le chemin d’accès et le nom du fichier de clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="44b24-122">After you do that, edit the **Key File** option in the advanced properties of the Linker to specify the path and name of the strong-name key file.</span></span>