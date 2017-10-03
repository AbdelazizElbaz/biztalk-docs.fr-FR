---
title: "Étape 8 : Créer un mappage avec le Mappeur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, maps
- creating, maps
- maps, creating
- BizTalk Mapper
ms.assetid: 785426c7-5651-48be-b3f4-7f9d8051ba23
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48e2578211d65ade2a50916e909c87a6fd84bf44
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-create-a-map-with-biztalk-mapper"></a><span data-ttu-id="42e93-102">Étape 8 : Créer un mappage avec le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="42e93-102">Step 8: Create a Map with BizTalk Mapper</span></span>
<span data-ttu-id="42e93-103">Dans cette étape, vous utilisez le Mappeur BizTalk pour créer un mappage.</span><span class="sxs-lookup"><span data-stu-id="42e93-103">In this step, you use the BizTalk Mapper to create a map.</span></span> <span data-ttu-id="42e93-104">Vous utilisez ce mappage pour créer des liens qui associent les données (champs) dans un document de demande de réapprovisionnement aux données dans une document de refus de la demande.</span><span class="sxs-lookup"><span data-stu-id="42e93-104">You use this map to create links that associate the data (fields) in a replenishment request document to the data in a request denied document.</span></span>  
  
### <a name="to-create-a-map"></a><span data-ttu-id="42e93-105">Pour créer un mappage</span><span class="sxs-lookup"><span data-stu-id="42e93-105">To create a map</span></span>  
  
1.  <span data-ttu-id="42e93-106">Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="42e93-106">In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="42e93-107">Dans le **ajouter un nouvel élément** boîte de dialogue le **catégories** volet, cliquez sur **les fichiers de mappage**.</span><span class="sxs-lookup"><span data-stu-id="42e93-107">In the **Add New Item** dialog box, in the **Categories** pane, click **Map Files**.</span></span>  
  
3.  <span data-ttu-id="42e93-108">Dans le **nom** , tapez **DoorbellMap** pour nommer la carte, puis cliquez sur **ajouter** pour démarrer le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="42e93-108">In the **Name** field, type **DoorbellMap** to name the map, and then click **Add** to start BizTalk Mapper.</span></span>  
  
4.  <span data-ttu-id="42e93-109">Dans le **schéma Source** volet (gauche), cliquez sur **ouvrir le schéma Source**.</span><span class="sxs-lookup"><span data-stu-id="42e93-109">In the **Source Schema** pane (left side), click **Open Source Schema**.</span></span>  
  
5.  <span data-ttu-id="42e93-110">Dans la boîte de dialogue Sélecteur de Type BizTalk, développez **BTAHL7 projet**, développez **schémas**, cliquez sur **BTAHL7_Project.Doorbell**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="42e93-110">In the BizTalk Type Picker dialog box, expand **BTAHL7 Project**, expand **Schemas**, click **BTAHL7_Project.Doorbell**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="42e93-111">Dans le **schéma de Destination** volet (à droite), cliquez sur **ouvrir le schéma de Destination**.</span><span class="sxs-lookup"><span data-stu-id="42e93-111">In the **Destination Schema** pane (right side), click **Open Destination Schema**.</span></span>  
  
7.  <span data-ttu-id="42e93-112">Dans le sélecteur de Type BizTalk, développez **BTAHL7 projet**, développez **schémas**, cliquez sur **BTAHL7Schemas.ADT_A04_22_GLO_DEF**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="42e93-112">In the BizTalk Type Picker, expand **BTAHL7 Project**, expand **Schemas**, click **BTAHL7Schemas.ADT_A04_22_GLO_DEF**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="42e93-113">Dans le **schéma de Destination** volet (à droite), développez **ADT_A04_22_GLO_DEF**, développez **PID_PatientIdentification**, développez **PID.5_PatientName** .</span><span class="sxs-lookup"><span data-stu-id="42e93-113">In the **Destination Schema** pane (right side), expand **ADT_A04_22_GLO_DEF**, expand **PID_PatientIdentification**, and expand **PID.5_PatientName**.</span></span>  
  
9. <span data-ttu-id="42e93-114">Dans le **schéma Source** volet (gauche), développez **DoorbellRoot**.</span><span class="sxs-lookup"><span data-stu-id="42e93-114">In the **Source Schema** pane (left side), expand **DoorbellRoot**.</span></span> <span data-ttu-id="42e93-115">Faites glisser le **LastName** au champ la **PN_0_FamilyName** champ dans le **schéma de Destination** volet.</span><span class="sxs-lookup"><span data-stu-id="42e93-115">Drag the **LastName** field to the **PN_0_FamilyName** field in the **Destination Schema** pane.</span></span>  
  
10. <span data-ttu-id="42e93-116">Dans le **schéma Source** volet, faites glisser le **FirstName** au champ la **PN_1_GivenName** champ dans le **schéma de Destination** volet.</span><span class="sxs-lookup"><span data-stu-id="42e93-116">In the **Source Schema** pane, drag the **FirstName** field to the **PN_1_GivenName** field in the **Destination Schema** pane.</span></span>  
  
11. <span data-ttu-id="42e93-117">Dans le **schéma Source** volet, faites glisser le **MiddleName** au champ la **PN_2_MiddleInitialOrName** champ dans le **schéma de Destination** volet .</span><span class="sxs-lookup"><span data-stu-id="42e93-117">In the **Source Schema** pane, drag the **MiddleName** field to the **PN_2_MiddleInitialOrName** field in the **Destination Schema** pane.</span></span>  
  
12. <span data-ttu-id="42e93-118">Dans le **schéma de Destination** volet, développez **PID_3_PatientIdInternalId**.</span><span class="sxs-lookup"><span data-stu-id="42e93-118">In the **Destination Schema** pane, expand **PID_3_PatientIdInternalId**.</span></span>  
  
13. <span data-ttu-id="42e93-119">Dans le **schéma Source** volet, faites glisser le **SSN** au champ la **CM_PAT_ID_0_PatientID** dans les **schéma de Destination** volet.</span><span class="sxs-lookup"><span data-stu-id="42e93-119">In the **Source Schema** pane, drag the **SSN** field to the **CM_PAT_ID_0_PatientID** in the **Destination Schema** pane.</span></span>  
  
14. <span data-ttu-id="42e93-120">Dans le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="42e93-120">In the **File** menu, click **Save All**.</span></span>  
  
 <span data-ttu-id="42e93-121">Dans un scénario d’enrichissement de message classique, si toutes les informations sur les patients manquantes, vous serez effectuer un appel à une base de données des enregistrements du Patient dans votre orchestration et ajoutez les informations manquantes, puis utilisez les informations supplémentaires pour terminer le mappage.</span><span class="sxs-lookup"><span data-stu-id="42e93-121">In a typical message enrichment scenario, if any patient information were missing, you would make a call to a Patient Records database in your orchestration and add the missing information, then use the additional information to complete the mapping.</span></span> <span data-ttu-id="42e93-122">Par exemple, vous pouvez extraire l’adresse d’un patient à partir de la base de données des enregistrements de Patient, car il n’a pas fourni par le message d’événement de déclencheur de sonnette XML entrant.</span><span class="sxs-lookup"><span data-stu-id="42e93-122">For example, you might retrieve the home address of a patient from the Patient Records database, since the inbound XML doorbell trigger event message did not provide it.</span></span>  
  
 <span data-ttu-id="42e93-123">Passez à [étape 9 : valider et générez le projet de la carte](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md).</span><span class="sxs-lookup"><span data-stu-id="42e93-123">Proceed to [Step 9: Validate and Build the Map Project](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e93-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42e93-124">See Also</span></span>  
 [<span data-ttu-id="42e93-125">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="42e93-125">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)