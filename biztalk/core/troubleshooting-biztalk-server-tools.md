---
title: "Dépannage des outils de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 038a5f5c-d6eb-42db-88d6-70f3deba7a8a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b7aedd8977042d15176781b0595bd5bb225a2fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-tools"></a><span data-ttu-id="5a7a5-102">Dépannage des outils BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="5a7a5-102">Troubleshooting BizTalk Server Tools</span></span>
<span data-ttu-id="5a7a5-103">Cette rubrique centralise les informations sur les problèmes connus rencontrés lors de l'utilisation des outils inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a7a5-103">This topic provides a centralized location for information about common problems encountered while using the tools included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="5a7a5-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="5a7a5-104">Known Issues</span></span>  
  
### <a name="biztalk-server-tools-and-utilities-may-not-function-correctly-on-a-windows-system-that-supports-uac"></a><span data-ttu-id="5a7a5-105">Les outils et utilitaires BizTalk Server peuvent ne pas fonctionner correctement sous un système Windows prenant en charge le contrôle de compte d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5a7a5-105">BizTalk Server Tools and Utilities May Not Function Correctly on a Windows System That Supports UAC</span></span>  
 <span data-ttu-id="5a7a5-106">**Problème**</span><span class="sxs-lookup"><span data-stu-id="5a7a5-106">**Problem**</span></span>  
  
 <span data-ttu-id="5a7a5-107">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur un système prenant en charge le contrôle de compte d'utilisateur, les outils inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent ne pas se lancer ou ne pas fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="5a7a5-107">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a system that supports User Account Control (UAC), the tools included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may not launch successfully, or may not function correctly.</span></span>  
  
 <span data-ttu-id="5a7a5-108">**Cause**</span><span class="sxs-lookup"><span data-stu-id="5a7a5-108">**Cause**</span></span>  
  
 <span data-ttu-id="5a7a5-109">Dans le cadre de l'exécution d'une application associée à un niveau de privilège spécifique, si le niveau requis est supérieur à celui de l'utilisateur qui exécute l'application, le contrôle de compte d'utilisateur affiche une invite permettant d'élever provisoirement le privilège de l'application au niveau requis.</span><span class="sxs-lookup"><span data-stu-id="5a7a5-109">When running an application that has been flagged for a specific privilege level, if the required level is higher than that of the user running the application, the UAC will display a prompt that allows you to temporarily elevate the application privilege to the required level.</span></span> <span data-ttu-id="5a7a5-110">Les outils intégrés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne sont pas associés aux indicateurs adéquats pour demander automatiquement une élévation de privilège. C'est pourquoi ils tentent de s'exécuter avec le niveau de privilège actuel de l'utilisateur exécutant l'application et échouent si un niveau de privilège supérieur est requis.</span><span class="sxs-lookup"><span data-stu-id="5a7a5-110">The tools shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] do not have the correct flags enabled to automatically request privilege elevation, so the tool will attempt to run at the current privilege level of the user running the application and will fail if a higher privilege level is required.</span></span>  
  
 <span data-ttu-id="5a7a5-111">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="5a7a5-111">**Resolution**</span></span>  
  
 <span data-ttu-id="5a7a5-112">Pour résoudre ce problème, exécutez tous les outils BizTalk Server avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="5a7a5-112">To resolve this problem, run all BizTalk Server tools with Administrative privileges.</span></span> <span data-ttu-id="5a7a5-113">Pour exécuter un outil avec des privilèges d’administrateur, cliquez sur l’application, puis sélectionnez **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="5a7a5-113">To run a tool with Administrative privileges, right-click the application and then select **Run as administrator**.</span></span>  
  
 <span data-ttu-id="5a7a5-114">Pour plus d’informations sur le contrôle de compte d’utilisateur, consultez [http://go.microsoft.com/fwlink/?LinkId=99167](http://go.microsoft.com/fwlink/?LinkId=99167).</span><span class="sxs-lookup"><span data-stu-id="5a7a5-114">For more information about the User Account Control, see [http://go.microsoft.com/fwlink/?LinkId=99167](http://go.microsoft.com/fwlink/?LinkId=99167).</span></span>  
  
### <a name="sometimes-biztalk-mapper-toolbox-may-appear-empty"></a><span data-ttu-id="5a7a5-115">La boîte à outils du Mappeur BizTalk apparaît parfois comme étant vide</span><span class="sxs-lookup"><span data-stu-id="5a7a5-115">Sometimes BizTalk Mapper Toolbox May Appear Empty</span></span>  
 <span data-ttu-id="5a7a5-116">**Problème**</span><span class="sxs-lookup"><span data-stu-id="5a7a5-116">**Problem**</span></span>  
  
 <span data-ttu-id="5a7a5-117">Parfois, lorsque vous ouvrez la boîte à outils du Mappeur dans Visual Studio, celle-ci ne contient aucun fonctoid.</span><span class="sxs-lookup"><span data-stu-id="5a7a5-117">Sometimes, when you open the Mapper toolbox in Visual Studio, you do not see any functoids in the toolbox.</span></span>  
  
 <span data-ttu-id="5a7a5-118">**Cause**</span><span class="sxs-lookup"><span data-stu-id="5a7a5-118">**Cause**</span></span>  
  
 <span data-ttu-id="5a7a5-119">Il se peut que des éléments soient endommagés lors de l'installation/désinstallation des compléments et/ou correctifs de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a7a5-119">Might be a probable corruption by install/uninstall of Visual Studio add-ins and/or patch(es).</span></span>  
  
 <span data-ttu-id="5a7a5-120">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="5a7a5-120">**Resolution**</span></span>  
  
 <span data-ttu-id="5a7a5-121">Pour rectifier ce problème :</span><span class="sxs-lookup"><span data-stu-id="5a7a5-121">To resolve this problem:</span></span>  
  
1.  <span data-ttu-id="5a7a5-122">Fermez toutes les instances en cours d’exécution de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a7a5-122">Close all running instances of Visual Studio.</span></span>  
  
2.  <span data-ttu-id="5a7a5-123">Démarrer **invite de commandes Visual Studio** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="5a7a5-123">Start **Visual Studio Command Prompt** as an administrator.</span></span>  
  
3.  <span data-ttu-id="5a7a5-124">À l'invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5a7a5-124">At the command prompt, type the following command:</span></span>  
  
    ```  
    devenv.exe /setup  
    ```