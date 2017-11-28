---
title: Page Ajouter une alerte | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0023ee8d-a0d1-4257-95c6-38c95060bd62
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa93a777481c905dbedfffe5e7675335c4aec40b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-alert-page"></a><span data-ttu-id="fa432-102">Page Ajouter une alerte</span><span class="sxs-lookup"><span data-stu-id="fa432-102">Add Alert Page</span></span>
<span data-ttu-id="fa432-103">Figure 1 montre la page Ajouter une alerte, où vous pouvez créer une nouvelle alerte qui déclenche le portail lorsqu’un message d’erreur correspondant aux critères (conditions) spécifiés dans l’alerte arrive sur le portail.</span><span class="sxs-lookup"><span data-stu-id="fa432-103">Figure 1 shows the Add Alert page, where you can create a new alert that the portal will raise when a fault message matching the criteria (conditions) specified in the alert arrives at the portal.</span></span>  
  
 <span data-ttu-id="fa432-104">![Page Ajouter une alerte](../esb-toolkit/media/ch8-addalertpage.gif "Ch8-AddAlertPage")</span><span class="sxs-lookup"><span data-stu-id="fa432-104">![Add Alert Page](../esb-toolkit/media/ch8-addalertpage.gif "Ch8-AddAlertPage")</span></span>  
  
 <span data-ttu-id="fa432-105">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="fa432-105">**Figure 1**</span></span>  
  
 <span data-ttu-id="fa432-106">**La page ESB Management Portal ajouter une alerte**</span><span class="sxs-lookup"><span data-stu-id="fa432-106">**The ESB Management Portal Add Alert page**</span></span>  
  
 <span data-ttu-id="fa432-107">Dans la page Ajouter une alerte, vous pouvez procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fa432-107">On the Add Alert page, you can do the following:</span></span>  
  
-   <span data-ttu-id="fa432-108">Tapez un nom pour la nouvelle alerte dans le **entrer le nom alerte** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="fa432-108">Type a name for the new alert in the **Enter Alert Name** text box.</span></span>  
  
-   <span data-ttu-id="fa432-109">Spécifier comment l’alerte est conformes aux valeurs des champs dans les exceptions entrantes dans le **ajouter des conditions de cette alerte** section de cette page.</span><span class="sxs-lookup"><span data-stu-id="fa432-109">Specify how the alert will match to values of the fields in incoming exceptions in the **Add conditions for this alert** section of this page.</span></span> <span data-ttu-id="fa432-110">Sélectionnez un champ à partir du schéma de l’exception (tel que **Application, le Type d’erreur,** ou **gravité d’erreur)** dans les **critères** liste déroulante, sélectionnez un type de comparaison pour le (par exemple, =, **! =, > =, < =,** ou **comme**) dans le **opérateur** liste déroulante ; et tapez ou sélectionnez une valeur dans la troisième liste.</span><span class="sxs-lookup"><span data-stu-id="fa432-110">Select a field from the exception schema (such as **Application, Error Type,** or **Fault Severity)** in the **Criteria** drop-down list; select a comparison type for the (such as =, **!=, >=, <=,** or **like**) in the **Operator** drop-down list; and type or select a value from the third list.</span></span> <span data-ttu-id="fa432-111">Lorsque vous sélectionnez un champ d’exception, le **valeur** contrôle change vers une zone de texte ou une liste déroulante, vous pouvez entrer ou sélectionner une valeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="fa432-111">When you select an exception field, the **Value** control changes to either a text box or a drop-down list for you to enter or select a matching value.</span></span>  
  
-   <span data-ttu-id="fa432-112">Après avoir sélectionné ou entrer les valeurs des critères, cliquez sur le **ajouter** lien pour ajouter cette condition à la liste dans le **Conditions** section de la page, puis répétez l’opération pour ajouter des conditions plus que vous avez besoin pour cette alerte .</span><span class="sxs-lookup"><span data-stu-id="fa432-112">After selecting or entering the criteria values, click the **Add** link to add this condition to the list in the **Conditions** section of the page, and repeat to add any more conditions you require for this alert.</span></span>  
  
-   <span data-ttu-id="fa432-113">Cliquez sur le **enregistrer** bouton permettant de créer la nouvelle alerte avec le nom et les conditions que vous avez spécifié.</span><span class="sxs-lookup"><span data-stu-id="fa432-113">Click the **Save** button to create the new alert with the name and conditions you specified.</span></span>