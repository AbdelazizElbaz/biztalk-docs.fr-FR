---
title: "L’authentification initiée par l’utilisation de l’utilitaire de suivi dans l’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host initiated SSO, trace utility
- trace utility
ms.assetid: a53444d1-3f63-42a6-8ee6-b60ff9af9e41
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebb2003cc6091e3f14bd863902e03649d9005722
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-use-the-trace-utility-in-host-initiated-sso"></a><span data-ttu-id="9e749-102">L’authentification initiée par l’utilisation de l’utilitaire de suivi dans l’hôte</span><span class="sxs-lookup"><span data-stu-id="9e749-102">How to Use the Trace Utility in Host Initiated SSO</span></span>
<span data-ttu-id="9e749-103">La principale méthode de résolution des problèmes est le suivi.</span><span class="sxs-lookup"><span data-stu-id="9e749-103">The primary method of troubleshooting is tracing.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="9e749-104">Suivi</span><span class="sxs-lookup"><span data-stu-id="9e749-104">Tracing</span></span>  
 <span data-ttu-id="9e749-105">Utilisez l'utilitaire de ligne de commande Suivi pour activer le suivi de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="9e749-105">Use the Trace command line utility to enable tracing in SSO.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e749-106">Pour que la commande de suivi fonctionne, le fichier tracelog.exe doivent être dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="9e749-106">For the trace command to function, the file tracelog.exe must be in the following directory:</span></span>  
>   
>  <span data-ttu-id="9e749-107">\<*lecteur*\>: \Program Files\Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="9e749-107">\<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e749-108">Vous pouvez télécharger ce fichier à partir de l’emplacement suivant : [http://go.microsoft.com/fwlink/?LinkId=59534](http://go.microsoft.com/fwlink/?LinkId=59534)</span><span class="sxs-lookup"><span data-stu-id="9e749-108">You can download this file from the following location: [http://go.microsoft.com/fwlink/?LinkId=59534](http://go.microsoft.com/fwlink/?LinkId=59534)</span></span>  
  
#### <a name="to-use-the-trace-utility"></a><span data-ttu-id="9e749-109">Pour utiliser l'utilitaire de suivi</span><span class="sxs-lookup"><span data-stu-id="9e749-109">To use the trace utility</span></span>  
  
1.  <span data-ttu-id="9e749-110">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="9e749-110">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="9e749-111">Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9e749-111">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="9e749-112">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="9e749-112">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="9e749-113">La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="9e749-113">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="9e749-114">Type **Trace – start – high** pour définir le niveau de suivi élevé et lancer le suivi.</span><span class="sxs-lookup"><span data-stu-id="9e749-114">Type **Trace –start –high** to set the tracing level to high and begin the trace.</span></span>  
  
5.  <span data-ttu-id="9e749-115">Exécutez le scénario avec une authentification unique initiée par l'hôte.</span><span class="sxs-lookup"><span data-stu-id="9e749-115">Run the scenario with host initiated SSO.</span></span>  
  
6.  <span data-ttu-id="9e749-116">Type **Trace – stop** à la fin de la trace.</span><span class="sxs-lookup"><span data-stu-id="9e749-116">Type **Trace –stop** to end the trace.</span></span> <span data-ttu-id="9e749-117">Un fichier .bin est généré dans le répertoire ci-dessus, que vous pouvez envoyer à Microsoft à des fins d'analyse.</span><span class="sxs-lookup"><span data-stu-id="9e749-117">A .bin file is generated in the directory above, which you can send to Microsoft for analysis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e749-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e749-118">See Also</span></span>  
 [<span data-ttu-id="9e749-119">Authentification unique initiée par l’hôte</span><span class="sxs-lookup"><span data-stu-id="9e749-119">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)