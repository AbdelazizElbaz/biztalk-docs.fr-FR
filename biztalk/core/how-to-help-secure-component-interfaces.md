---
title: "Interfaces de façon sécurisée de composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- component interfaces, helping to secure
- security, component interfaces
ms.assetid: 03b2af44-78e7-4fdc-bfa3-7697b2a60986
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54136aaeae9578ae4e438c5bd8b95b902d618f96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-help-secure-component-interfaces"></a><span data-ttu-id="31eee-102">Sécurisation des interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="31eee-102">How to Help Secure Component Interfaces</span></span>
<span data-ttu-id="31eee-103">Avant de pouvoir commencer à tester une interface de composant, vous devez en configurer la sécurité.</span><span class="sxs-lookup"><span data-stu-id="31eee-103">Before you can start testing a component interface, you must set up security for it.</span></span> <span data-ttu-id="31eee-104">La procédure suivante décrit comment configurer la sécurité d’interface de composant pour PeopleSoft Version 8.4, mais vous pouvez utiliser la procédure pour la Version 8.1.</span><span class="sxs-lookup"><span data-stu-id="31eee-104">The following procedure describes how to configure component interface security for PeopleSoft Version 8.4, but you can use the procedure for Version 8.1.</span></span>  
  
### <a name="to-configure-interface-security"></a><span data-ttu-id="31eee-105">Pour configurer la sécurité de l'interface</span><span class="sxs-lookup"><span data-stu-id="31eee-105">To configure interface security</span></span>  
  
1.  <span data-ttu-id="31eee-106">Développez **PeopleTools**, développez **sécurité**, développez **profils utilisateur**, puis développez **autorisations et rôles**.</span><span class="sxs-lookup"><span data-stu-id="31eee-106">Expand **PeopleTools**, expand **Security**, expand **User Profiles**, and then expand **Permissions & Roles**.</span></span>  
  
     ![](../core/media/psadapter-47-ps-configsecurity1.gif "PSAdapter_47_PS_ConfigSecurity1")  
  
2.  <span data-ttu-id="31eee-107">Cliquez sur **listes d’autorisations**.</span><span class="sxs-lookup"><span data-stu-id="31eee-107">Click **Permission Lists**.</span></span>  
  
3.  <span data-ttu-id="31eee-108">Cliquez sur **Rechercher**.</span><span class="sxs-lookup"><span data-stu-id="31eee-108">Click **Search**.</span></span>  
  
     ![](../core/media/psadapter-48-ps-configsecurity2.gif "PSAdapter_48_PS_ConfigSecurity2")  
  
4.  <span data-ttu-id="31eee-109">Dans le **recherche des listes des autorisations** volet, sélectionnez la liste des autorisations appropriées.</span><span class="sxs-lookup"><span data-stu-id="31eee-109">In the **Permission Lists Search** pane, select the relevant permission list.</span></span>  
  
     <span data-ttu-id="31eee-110">La fenêtre suivante s'affiche.</span><span class="sxs-lookup"><span data-stu-id="31eee-110">The following window appears.</span></span>  
  
     ![](../core/media/psadapter-49-ps-configsecurity3.gif "PSAdapter_49_PS_ConfigSecurity3")  
  
5.  <span data-ttu-id="31eee-111">Cliquez sur la flèche droite en regard du **heures de connexion** onglet pour afficher plus d’onglets.</span><span class="sxs-lookup"><span data-stu-id="31eee-111">Click the right arrow next to the **Sign-on Times** tab to display more tabs.</span></span>  
  
     ![](../core/media/psadapter-50-ps-configsecurity4.gif "PSAdapter_50_PS_ConfigSecurity4")  
  
6.  <span data-ttu-id="31eee-112">Cliquez sur le **Interfaces de composant** onglet.</span><span class="sxs-lookup"><span data-stu-id="31eee-112">Click the **Component Interfaces** tab.</span></span>  
  
7.  <span data-ttu-id="31eee-113">Cliquez sur le + (signe) pour ajouter une nouvelle ligne à la **Interfaces de composant** liste.</span><span class="sxs-lookup"><span data-stu-id="31eee-113">Click the + (plus) sign to add a new row to the **Component Interfaces** list.</span></span>  
  
     <span data-ttu-id="31eee-114">Dans le champ qui s'affiche, vous pouvez taper le nom de l'interface de composant.</span><span class="sxs-lookup"><span data-stu-id="31eee-114">A field appears in which you can type the component interface name.</span></span>  
  
     ![](../core/media/psadapter-51-ps-configsecurity5.gif "PSAdapter_51_PS_ConfigSecurity5")  
  
8.  <span data-ttu-id="31eee-115">Tapez le nom d’interface de composant, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="31eee-115">Type the component interface name, and then click **Edit**.</span></span>  
  
     <span data-ttu-id="31eee-116">Cet exemple utilise l'interface de composant AR_ITEM_AGENT.</span><span class="sxs-lookup"><span data-stu-id="31eee-116">This example uses component interface AR_ITEM_AGENT.</span></span>  
  
     ![](../core/media/psadapter-52-ps-configsecurity6.gif "PSAdapter_52_PS_ConfigSecurity6")  
  
9. <span data-ttu-id="31eee-117">Dans la liste, sélectionnez le niveau d’accès souhaité pour chaque méthode, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="31eee-117">In the list, select the desired access level for each method, and then click **OK**.</span></span>  
  
     <span data-ttu-id="31eee-118">La fenêtre suivante s'affiche.</span><span class="sxs-lookup"><span data-stu-id="31eee-118">The following window appears.</span></span>  
  
     ![](../core/media/psadapter-53-ps-configsecurity7.gif "PSAdapter_53_PS_ConfigSecurity7")  
  
10. <span data-ttu-id="31eee-119">Faites défiler vers le bas dans le volet droit, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="31eee-119">Scroll down in the right pane, and click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31eee-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31eee-120">See Also</span></span>  
 <span data-ttu-id="31eee-121">[Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md) </span><span class="sxs-lookup"><span data-stu-id="31eee-121">[Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md) </span></span>  
 [<span data-ttu-id="31eee-122">Annexe c : à l’aide des Interfaces de composant</span><span class="sxs-lookup"><span data-stu-id="31eee-122">Appendix C: Using Component Interfaces</span></span>](../core/appendix-c-using-component-interfaces.md)