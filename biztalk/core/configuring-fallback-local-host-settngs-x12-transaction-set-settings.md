---
title: "Configuration Settngs de secours de l’hôte Local (paramètres X12-Transaction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68511199-a7ed-45b3-807d-70378b2c6ebb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fa9e1fcc8bf1764a16142d38058e14878341fdc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-local-host-settngs-x12-transaction-set-settings"></a><span data-ttu-id="62976-102">Configuration des paramètres de secours de l'hôte local (X12 - Paramètres de documents informatisés)</span><span class="sxs-lookup"><span data-stu-id="62976-102">Configuring Fallback Local Host Settngs (X12-Transaction Set Settings)</span></span>
<span data-ttu-id="62976-103">Pour traiter un échange entrant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit déterminer le schéma dont il a besoin pour le traitement et la validation de l'échange.</span><span class="sxs-lookup"><span data-stu-id="62976-103">To process an incoming interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must determine the schema that it needs to use in processing and validating the interchange.</span></span> <span data-ttu-id="62976-104">Pour ce faire, il doit déterminer l'espace de noms cible associé au schéma, ainsi que le schéma à utiliser.</span><span class="sxs-lookup"><span data-stu-id="62976-104">This consists of determining the target namespace associated with the schema, and determining the schema to be used.</span></span> <span data-ttu-id="62976-105">Dans cette page de propriétés de secours, vous indiquez l'espace de noms cible de secours.</span><span class="sxs-lookup"><span data-stu-id="62976-105">In this page of the fallback agreement, you specify the fallback target namespace.</span></span> <span data-ttu-id="62976-106">Comment [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine le schéma est décrit dans [résolution de l’accord, détection de schéma et l’autorisation pour les Messages EDI reçus](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span><span class="sxs-lookup"><span data-stu-id="62976-106">How [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] determines the schema is described in [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62976-107">Cette rubrique s'applique également aux paramètres liés à HIPAA.</span><span class="sxs-lookup"><span data-stu-id="62976-107">This topic applies also to HIPAA-related settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="62976-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="62976-108">Prerequisites</span></span>  
 <span data-ttu-id="62976-109">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="62976-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a><span data-ttu-id="62976-110">Pour configurer les paramètres de l'hôte local des documents informatisés</span><span class="sxs-lookup"><span data-stu-id="62976-110">To configure local host settings for transaction sets</span></span>  
  
1.  <span data-ttu-id="62976-111">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.</span><span class="sxs-lookup"><span data-stu-id="62976-111">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="62976-112">Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres des documents informatisés** , cliquez sur **paramètres d’hôte Local** .</span><span class="sxs-lookup"><span data-stu-id="62976-112">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Transaction Set Settings** section, click **Local Host Settings**.</span></span>  
  
3.  <span data-ttu-id="62976-113">Sélectionnez **conversion implicite de base 10 de valeur numérique de format décimal** pour convertir un nombre EDI spécifié au format Nn en une valeur numérique de base 10 dans le fichier XML intermédiaire dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="62976-113">Select **Convert implied decimal format Nn to base 10 numeric value** to convert an EDI number that is specified with the format Nn into a base-10 numeric value in the intermediate XML in BizTalk Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="62976-114">Une fois la conversion effectuée, la validation de la longueur du fichier XML intermédiaire peut échouer.</span><span class="sxs-lookup"><span data-stu-id="62976-114">After this conversion, the intermediate XML may fail length validation.</span></span> <span data-ttu-id="62976-115">Cela peut se produire car la valeur numérique en base 10 contient une virgule, ce qui la rend plus longue que le format Nn.</span><span class="sxs-lookup"><span data-stu-id="62976-115">This occurs because the number in the base-10 numeric format includes a decimal, making its length one greater than the number in Nn format.</span></span> <span data-ttu-id="62976-116">Vous pouvez résoudre ce problème en ajoutant une valeur de **1** à la valeur de longueur minimale/maximale.</span><span class="sxs-lookup"><span data-stu-id="62976-116">You can resolve this issue by adding a value of **1** to the minimum/maximum length value.</span></span>  
  
4.  <span data-ttu-id="62976-117">Sélectionnez **créer des balises XML vides pour les séparateurs de fin** pour que l’expéditeur des échanges inclue des balises XML vides pour les séparateurs de fin.</span><span class="sxs-lookup"><span data-stu-id="62976-117">Select **Create empty XML tags for trailing separators** to have the interchange sender include empty XML tags for trailing separators.</span></span>  
  
5.  <span data-ttu-id="62976-118">Pour **cible Namespace**, entrez (ou sélectionnez dans la liste déroulante) l’espace de noms cible qui [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise pour déterminer le schéma pour traiter le message reçu avec.</span><span class="sxs-lookup"><span data-stu-id="62976-118">For **Target Namespace**, enter (or select from the drop-down list) the target namespace that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses to determine the schema to process the received message with.</span></span>  
  
6.  <span data-ttu-id="62976-119">Cliquez sur **appliquer** pour accepter les modifications, ou cliquez sur **OK** pour entrer et valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="62976-119">Click **Apply** to accept the changes, or click **OK** to enter and validate the changes, and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62976-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62976-120">See Also</span></span>  
 [<span data-ttu-id="62976-121">Configuration X12 définir les propriétés de l’accord de secours pour la Transaction paramètres</span><span class="sxs-lookup"><span data-stu-id="62976-121">Configuring X12 Fallback Agreement Properties for Transaction Set Settings</span></span>](../core/configuring-x12-fallback-agreement-properties-for-transaction-set-settings.md)