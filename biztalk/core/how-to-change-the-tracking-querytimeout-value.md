---
title: Comment modifier la valeur QueryTimeout du suivi | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [HAT], time-out limits
- HAT, time-out limits
ms.assetid: abc26f37-6537-42fa-81ff-bc8b758b4e10
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca9f61466323e0b154bdeb0499cc5cee6e4ef10c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-tracking-querytimeout-value"></a><span data-ttu-id="ee1a0-102">Modification de la valeur QueryTimeout du suivi</span><span class="sxs-lookup"><span data-stu-id="ee1a0-102">How to Change the Tracking QueryTimeout Value</span></span>
<span data-ttu-id="ee1a0-103">Par défaut, le suivi des messages et des instances de service expire si une requête s'exécute pendant plus de 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-103">By default, message and service instance tracking will time out if a query runs longer than 60 seconds.</span></span> <span data-ttu-id="ee1a0-104">Vous pouvez modifier cette valeur dans le registre afin que les requêtes puissent s'exécuter pendant plus de 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-104">You can change the timeout value in the registry to enable queries to run longer than 60 seconds.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ee1a0-105">Une modification incorrecte du Registre peut sérieusement endommager votre système.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-105">Incorrectly editing the registry may severely damage your system.</span></span> <span data-ttu-id="ee1a0-106">Avant d'apporter des modifications au Registre, il convient de sauvegarder les données importantes qui se trouvent sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-106">Before making changes to the registry, you should back up any valued data on the computer.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ee1a0-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ee1a0-107">Prerequisites</span></span>  
 <span data-ttu-id="ee1a0-108">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-108">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
### <a name="to-change-the-query-timeout-value"></a><span data-ttu-id="ee1a0-109">Pour modifier la valeur du délai de la requête</span><span class="sxs-lookup"><span data-stu-id="ee1a0-109">To change the query timeout value</span></span>  
  
1.  <span data-ttu-id="ee1a0-110">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **regedit**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-110">Click **Start**, click **Run**, type **regedit**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="ee1a0-111">Dans l'Éditeur du Registre, recherchez la sous-clé suivante, puis cliquez dessus :</span><span class="sxs-lookup"><span data-stu-id="ee1a0-111">In Registry Editor, locate and then click the following subkey:</span></span>  
  
     <span data-ttu-id="ee1a0-112">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3. 0**</span><span class="sxs-lookup"><span data-stu-id="ee1a0-112">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0**</span></span>  
  
3.  <span data-ttu-id="ee1a0-113">S'il existe une sous-clé de suivi, passez à l'étape 6.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-113">If there is a Tracking subkey, go to step 6.</span></span>  
  
4.  <span data-ttu-id="ee1a0-114">Pour créer une sous-clé de suivi sur le **modifier** menu, pointez sur **nouveau**, puis cliquez sur **clé**.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-114">To create a Tracking subkey, on the **Edit** menu, point to **New**, and then click **Key**.</span></span>  
  
5.  <span data-ttu-id="ee1a0-115">Type **suivi**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-115">Type **Tracking**, and then press ENTER.</span></span>  
  
6.  <span data-ttu-id="ee1a0-116">Recherchez la sous-clé suivante, puis cliquez dessus :</span><span class="sxs-lookup"><span data-stu-id="ee1a0-116">Locate and then click the following subkey:</span></span>  
  
     <span data-ttu-id="ee1a0-117">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Tracking**</span><span class="sxs-lookup"><span data-stu-id="ee1a0-117">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Tracking**</span></span>  
  
7.  <span data-ttu-id="ee1a0-118">Sur le **modifier** menu, pointez sur **nouveau**, puis cliquez sur **valeur DWORD**.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-118">On the **Edit** menu, point to **New**, and then click **DWORD Value**.</span></span>  
  
8.  <span data-ttu-id="ee1a0-119">Type **ConnectionTimeout**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-119">Type **ConnectionTimeout**, and then press ENTER.</span></span>  
  
9. <span data-ttu-id="ee1a0-120">Avec le bouton droit **ConnectionTimeout**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-120">Right-click **ConnectionTimeout**, and then click **Modify**.</span></span>  
  
10. <span data-ttu-id="ee1a0-121">Dans le **modifier la valeur DWORD** boîte de dialogue, cliquez sur **décimal**.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-121">In the **Edit DWORD Value** dialog box, click **Decimal**.</span></span>  
  
11. <span data-ttu-id="ee1a0-122">Dans le **données de la valeur** zone, tapez la valeur en secondes pendant laquelle vous souhaitez définir pour la valeur de délai d’attente de requête, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-122">In the **Value data** box, type the value in seconds that you want to set for the query timeout value, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="ee1a0-123">Dans le menu **Fichier** , cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-123">On the **File** menu, click **Exit**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ee1a0-124">Il se peut que vous deviez fermer, puis rouvrir la console Administration de BizTalk Server pour que la nouvelle valeur soit prise en compte.</span><span class="sxs-lookup"><span data-stu-id="ee1a0-124">You may need to close and then reopen the BizTalk Server Administration Console in order for the new timeout value to take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1a0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee1a0-125">See Also</span></span>  
 [<span data-ttu-id="ee1a0-126">Affichage des données historiques et de suivi</span><span class="sxs-lookup"><span data-stu-id="ee1a0-126">Viewing Historical and Tracked Data</span></span>](../core/viewing-historical-and-tracked-data.md)