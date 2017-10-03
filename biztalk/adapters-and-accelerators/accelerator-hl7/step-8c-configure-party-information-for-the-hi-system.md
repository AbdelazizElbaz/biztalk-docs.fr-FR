---
title: "Étape 8C : configurer les informations de tiers pour le système HI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ac5c113-7ee7-4009-8ca3-d263f74c7a8d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f0b9e1538ea667eab2299a1a02021c1237bc985
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8c-configure-party-information-for-the-hi-system"></a><span data-ttu-id="f887a-102">Étape 8C : configurer les informations de tiers pour le système HI</span><span class="sxs-lookup"><span data-stu-id="f887a-102">Step 8C: Configure Party Information for the HI System</span></span>
<span data-ttu-id="f887a-103">Dans cette étape, vous configurez les informations de tiers pour le système HI.</span><span class="sxs-lookup"><span data-stu-id="f887a-103">In this step, you configure the party information for the HI System.</span></span>  
  
### <a name="to-configure-the-hi-system-party-information"></a><span data-ttu-id="f887a-104">Pour configurer les informations de tiers HI système</span><span class="sxs-lookup"><span data-stu-id="f887a-104">To configure the HI System party information</span></span>  
  
1.  <span data-ttu-id="f887a-105">Dans la Console Administration de BizTalk Server, cliquez sur **Parties**, pointez sur **nouveau**, puis cliquez sur **tiers**.</span><span class="sxs-lookup"><span data-stu-id="f887a-105">In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="f887a-106">Dans la boîte de dialogue Propriétés du tiers dans le **nom** , tapez **Tutorial_HISystem**.</span><span class="sxs-lookup"><span data-stu-id="f887a-106">In the Party Properties dialog box, in the **Name** box, type **Tutorial_HISystem**.</span></span>  
  
3.  <span data-ttu-id="f887a-107">Dans l’arborescence de la console, cliquez sur **Ports d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="f887a-107">In the console tree, click **Send Ports**.</span></span>  
  
4.  <span data-ttu-id="f887a-108">Dans le volet Ports d’envoi, cliquez sur le champ vide dans le **nom** colonne, sélectionnez **Tutorial_MllpSend**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f887a-108">In the Send Ports pane, click the blank field in the **Name** column, select **Tutorial_MllpSend**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="f887a-109">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour HL7**, puis cliquez sur **BTAHL7 L’Explorateur de configuration**.</span><span class="sxs-lookup"><span data-stu-id="f887a-109">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
6.  <span data-ttu-id="f887a-110">Dans l’Explorateur de Configuration BTAHL7, sélectionnez le **MSH carte** onglet, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f887a-110">In BTAHL7 Configuration Explorer, select the **MSH Map** tab, and then do the following:</span></span>  
  
    |<span data-ttu-id="f887a-111">Utiliser</span><span class="sxs-lookup"><span data-stu-id="f887a-111">Use this</span></span>|<span data-ttu-id="f887a-112">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="f887a-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="f887a-113">**MSH3**</span><span class="sxs-lookup"><span data-stu-id="f887a-113">**MSH3**</span></span>|<span data-ttu-id="f887a-114">Type **BTAHL7**, **IE**, et **UUID** dans la première, deuxième et troisième messages, respectivement.</span><span class="sxs-lookup"><span data-stu-id="f887a-114">Type **BTAHL7**, **IE**, and **UUID** in the first, second, and third message boxes, respectively.</span></span>|  
    |<span data-ttu-id="f887a-115">**MSH5**</span><span class="sxs-lookup"><span data-stu-id="f887a-115">**MSH5**</span></span>|<span data-ttu-id="f887a-116">Type **HI**, **système**, et **GUID** dans la première, deuxième et troisième messages, respectivement.</span><span class="sxs-lookup"><span data-stu-id="f887a-116">Type **HI**, **System**, and **GUID** in the first, second, and third message boxes, respectively.</span></span>|  
    |<span data-ttu-id="f887a-117">**MSH9**</span><span class="sxs-lookup"><span data-stu-id="f887a-117">**MSH9**</span></span>|<span data-ttu-id="f887a-118">Type **ADT** et **A04** dans les zones de message de premier et deuxième, respectivement.</span><span class="sxs-lookup"><span data-stu-id="f887a-118">Type **ADT** and **A04** in the first and second message boxes, respectively.</span></span>|  
    |<span data-ttu-id="f887a-119">**MSH12**</span><span class="sxs-lookup"><span data-stu-id="f887a-119">**MSH12**</span></span>|<span data-ttu-id="f887a-120">Type **2.4**.</span><span class="sxs-lookup"><span data-stu-id="f887a-120">Type **2.4**.</span></span>|  
    |<span data-ttu-id="f887a-121">**MSH15**</span><span class="sxs-lookup"><span data-stu-id="f887a-121">**MSH15**</span></span>|<span data-ttu-id="f887a-122">Sélectionnez **SU** pour envoyer des accusés de réception après la transmission réussie d’un message.</span><span class="sxs-lookup"><span data-stu-id="f887a-122">Select **SU** to send acknowledgments after successful transmission of a message.</span></span>|  
    |<span data-ttu-id="f887a-123">**MSH16**</span><span class="sxs-lookup"><span data-stu-id="f887a-123">**MSH16**</span></span>|<span data-ttu-id="f887a-124">Sélectionnez **Because** pour ne jamais envoyer les accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="f887a-124">Select **NE** to never send acknowledgments.</span></span>|  
  
7.  <span data-ttu-id="f887a-125">Cliquez sur **enregistrer**, puis fermez l’Explorateur de Configuration BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="f887a-125">Click **Save**, and then close the BTAHL7 Configuration Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f887a-126">Il est inutile de créer des informations de tiers pour le système de moteur Interface BTAHL7, car les informations de configuration ne sont pas nécessaires pour ce scénario.</span><span class="sxs-lookup"><span data-stu-id="f887a-126">You do not need to create party information for the BTAHL7 Interface Engine System, because configuration information is not required for this scenario.</span></span>  
  
 <span data-ttu-id="f887a-127">Passez à [étape 9 : redémarrez BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="f887a-127">Proceed to [Step 9: Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-9-restart-biztalk-server.md).</span></span>