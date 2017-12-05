---
title: "Création, affichage et suppression d’erreur des alertes de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59df2b40-b42c-4167-873c-0819839919da
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55894eca1baa8ca6616c67f623a87e8015a2f32f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-viewing-and-deleting-fault-message-alerts"></a><span data-ttu-id="208b6-102">Création, affichage et suppression d’alertes de Message d’erreur</span><span class="sxs-lookup"><span data-stu-id="208b6-102">Creating, Viewing, and Deleting Fault Message Alerts</span></span>
<span data-ttu-id="208b6-103">Le portail de gestion ESB peut générer des alertes lors de l’arrivent de messages d’erreur sur le portail, basée sur une comparaison de valeurs dans le message avec les critères spécifiés pour l’alerte.</span><span class="sxs-lookup"><span data-stu-id="208b6-103">The ESB Management Portal can generate alerts when fault messages arrive at the portal, based on a comparison of values in the message with criteria specified for the alert.</span></span> <span data-ttu-id="208b6-104">Le portail peut également conserver une liste des notifications d’alertes liées aux différents utilisateurs, et il informe ces utilisateurs lors de façon proactive, il déclenche des alertes.</span><span class="sxs-lookup"><span data-stu-id="208b6-104">The portal can also maintain a list of notifications linked to individual alerts and users, and it will notify these users when it proactively raises alerts.</span></span>  
  
### <a name="to-create-and-configure-a-new-alert"></a><span data-ttu-id="208b6-105">Pour créer et configurer une nouvelle alerte</span><span class="sxs-lookup"><span data-stu-id="208b6-105">To create and configure a new alert</span></span>  
  
1.  <span data-ttu-id="208b6-106">Ouvrez le [Page alertes du portail](../esb-toolkit/portal-alerts-page.md) pour afficher une liste des alertes existantes et vos abonnements en cours pour ces alertes.</span><span class="sxs-lookup"><span data-stu-id="208b6-106">Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md) to see a list of existing alerts and your current subscriptions to these alerts.</span></span>  
  
2.  <span data-ttu-id="208b6-107">Cliquez sur le **créer une alerte** lien pour ouvrir la [ajouter une Page d’alerte](../esb-toolkit/add-alert-page.md).</span><span class="sxs-lookup"><span data-stu-id="208b6-107">Click the **Create Alert** link to open the [Add Alert Page](../esb-toolkit/add-alert-page.md).</span></span>  
  
3.  <span data-ttu-id="208b6-108">Dans le **entrer le nom alerte** zone de texte, tapez un nom pour la nouvelle alerte.</span><span class="sxs-lookup"><span data-stu-id="208b6-108">In the **Enter Alert Name** text box, type a name for the new alert.</span></span>  
  
4.  <span data-ttu-id="208b6-109">Dans le **Conditions** section de la page Ajouter une alerte, sélectionnez un champ (tel que **Application**, **Type d’erreur**, ou **gravité d’erreur**) dans le **Critères** liste déroulante ; Sélectionnez un type de comparaison (tels que +, =, ! =, > =, < =, ou **comme**) dans le **opérateur** liste déroulante ; et tapez ou sélectionnez un valeur de la troisième liste ou zone de texte (nommées **valeur**).</span><span class="sxs-lookup"><span data-stu-id="208b6-109">In the **Conditions** section of the Add Alert page, select a field (such as **Application**, **Error Type**, or **Fault Severity**) in the **Criteria** drop-down list; select a comparison type (such as +, =, !=, >=, <=, or **like**) in the **Operator** drop-down list; and type or select a value from the third list or text box (named **Value**).</span></span> <span data-ttu-id="208b6-110">Lorsque vous sélectionnez un **critères** valeur, les modifications de la page pour afficher une zone de texte ou d’une liste déroulante pour la valeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="208b6-110">As you select a **Criteria** value, the page changes to display either a text box or a drop-down list for the matching value.</span></span> <span data-ttu-id="208b6-111">Toutes les conditions sont combinées à l’aide de la **AND** opérateur.</span><span class="sxs-lookup"><span data-stu-id="208b6-111">All conditions are combined using the **AND** operator.</span></span>  
  
5.  <span data-ttu-id="208b6-112">Cliquez sur le **ajouter** ce lien pour ajouter cette condition à la liste, puis répétez l’étape précédente pour ajouter d’autres conditions si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="208b6-112">Click the **Add** link to add this condition to the list, and then repeat the previous step to add more conditions if required.</span></span>  
  
6.  <span data-ttu-id="208b6-113">Cliquez sur le **enregistrer** bouton permettant de créer une nouvelle alerte avec le nom spécifié et les conditions.</span><span class="sxs-lookup"><span data-stu-id="208b6-113">Click the **Save** button to create a new alert with the specified name and conditions.</span></span>  
  
### <a name="to-view-details-of-an-existing-alert-or-delete-an-existing-alert"></a><span data-ttu-id="208b6-114">Pour afficher les détails d’une alerte existante ou supprimer une alerte existante</span><span class="sxs-lookup"><span data-stu-id="208b6-114">To view details of an existing alert or delete an existing alert</span></span>  
  
1.  <span data-ttu-id="208b6-115">Ouvrez le [Page alertes du portail](../esb-toolkit/portal-alerts-page.md).</span><span class="sxs-lookup"><span data-stu-id="208b6-115">Open the [Portal Alerts Page](../esb-toolkit/portal-alerts-page.md).</span></span>  
  
2.  <span data-ttu-id="208b6-116">Pour supprimer une alerte, cliquez sur le **supprimer l’alerte** icône dans la colonne d’Action d’une alerte existante.</span><span class="sxs-lookup"><span data-stu-id="208b6-116">To delete an alert, click the **Delete Alert** icon in the Action column of an existing alert.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="208b6-117">Utilisateurs non-administrateurs peuvent supprimer uniquement les alertes pour laquelle ils sont propriétaires, et pour lesquels il n’existe actuellement aucun abonné.</span><span class="sxs-lookup"><span data-stu-id="208b6-117">Non-administrative users can delete only alerts for which they are an owner, and for which there are currently no subscribers.</span></span> <span data-ttu-id="208b6-118">Vous devez vous connecter au portail en tant qu’administrateur pour supprimer les autres alertes.</span><span class="sxs-lookup"><span data-stu-id="208b6-118">You must log on to the portal as an administrator to delete other alerts.</span></span>  
  
3.  <span data-ttu-id="208b6-119">Pour afficher les détails d’une alerte, cliquez sur le **vue** icône dans la colonne d’Action d’une alerte existante.</span><span class="sxs-lookup"><span data-stu-id="208b6-119">To view details of an alert, click the **View** icon in the Action column of an existing alert.</span></span> <span data-ttu-id="208b6-120">Cela ouvre la page Afficheur des alertes.</span><span class="sxs-lookup"><span data-stu-id="208b6-120">This opens the Alert Viewer page.</span></span>  
  
4.  <span data-ttu-id="208b6-121">Cliquez sur **exporter vers Excel** pour télécharger la liste complète des alertes dans un format que vous pouvez afficher dans Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="208b6-121">Click **Export To Excel** to download the complete list of alerts in a format that you can view in Microsoft Excel.</span></span>