---
title: "Configuration des paramètres de secours de l’hôte Local (EDIFACT-informatisés paramètres) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0142b3fc-009f-4da5-b34d-dddf4fb96e0f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 931db62edda264a6fff0ddb422bd41b243cd29ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-local-host-settings-edifact-transaction-set-settings"></a><span data-ttu-id="7b249-102">Configuration des paramètres d'hôte local de secours (EDIFACT-Paramètres de documents informatisés)</span><span class="sxs-lookup"><span data-stu-id="7b249-102">Configuring Fallback Local Host Settings (EDIFACT-Transaction Set Settings)</span></span>
<span data-ttu-id="7b249-103">Pour traiter un échange entrant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit déterminer le schéma dont il a besoin pour le traitement et la validation de l'échange.</span><span class="sxs-lookup"><span data-stu-id="7b249-103">To process an incoming interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must determine the schema that it needs to use in processing and validating the interchange.</span></span> <span data-ttu-id="7b249-104">Pour ce faire, il doit déterminer l'espace de noms cible associé au schéma, ainsi que le schéma à utiliser.</span><span class="sxs-lookup"><span data-stu-id="7b249-104">This consists of determining the target namespace associated with the schema, and determining the schema to be used.</span></span> <span data-ttu-id="7b249-105">Dans cette page de propriétés de secours, vous entrez les propriétés à utiliser pour déterminer l'espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="7b249-105">In this page of fallback agreement, you enter the properties to be used in determining the target namespace.</span></span> <span data-ttu-id="7b249-106">Comment BizTalk Server détermine le schéma est décrite dans [résolution de l’accord, détection de schéma et l’autorisation pour les Messages EDI reçus](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span><span class="sxs-lookup"><span data-stu-id="7b249-106">How BizTalk Server determines the schema is described in [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7b249-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7b249-107">Prerequisites</span></span>  
 <span data-ttu-id="7b249-108">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b249-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a><span data-ttu-id="7b249-109">Pour configurer les paramètres de l'hôte local des documents informatisés</span><span class="sxs-lookup"><span data-stu-id="7b249-109">To configure local host settings for transaction sets</span></span>  
  
1.  <span data-ttu-id="7b249-110">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.</span><span class="sxs-lookup"><span data-stu-id="7b249-110">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="7b249-111">Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres des documents informatisés** , cliquez sur **hôte Local Paramètres**.</span><span class="sxs-lookup"><span data-stu-id="7b249-111">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Transaction Set Settings** section, click **Local Host Settings**.</span></span>  
  
3.  <span data-ttu-id="7b249-112">Sélectionnez **créer des balises XML vides pour les séparateurs de fin** pour que l’expéditeur des échanges inclue des balises XML vides pour les séparateurs de fin.</span><span class="sxs-lookup"><span data-stu-id="7b249-112">Select **Create empty XML tags for trailing separators** to have the interchange sender include empty XML tags for trailing separators.</span></span>  
  
4.  <span data-ttu-id="7b249-113">Sélectionnez **utiliser le point (.) comme séparateur décimal** pour activer BizTalk Server incluent un point (.) dans le message XML créé à partir d’un échange contenant un nombre décimal.</span><span class="sxs-lookup"><span data-stu-id="7b249-113">Select **Use Dot (.) as decimal separator** to enable BizTalk Server include a dot (.) in the XML message created out of an interchange that contains a decimal number.</span></span>  
  
5.  <span data-ttu-id="7b249-114">Pour **cible Namespace**, entrez (ou sélectionnez dans la liste déroulante) l’espace de noms cible qui [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise pour déterminer le schéma à traiter le message reçu avec</span><span class="sxs-lookup"><span data-stu-id="7b249-114">For **Target Namespace**, enter (or select from the drop-down list) the target namespace that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to determine the schema to process the received message with</span></span>  
  
6.  <span data-ttu-id="7b249-115">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="7b249-115">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b249-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b249-116">See Also</span></span>  
 [<span data-ttu-id="7b249-117">Configuration des propriétés d’accord de secours EDIFACT Transaction définie les paramètres</span><span class="sxs-lookup"><span data-stu-id="7b249-117">Configuring EDIFACT Fallback Agreement Properties for Transaction Set Settings</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-transaction-set-settings.md)