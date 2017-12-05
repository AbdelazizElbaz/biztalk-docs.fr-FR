---
title: "Configuration des documents informatisés (EDIFACT) de liste | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b03ace75-70bf-47c9-9a94-df813d7cab1e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a95feac48f7cb5137e95a34bf46c38811bb75c51
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-transaction-set-list-edifact"></a><span data-ttu-id="37c60-102">Configuration de la liste des documents informatisés (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="37c60-102">Configuring Transaction Set List (EDIFACT)</span></span>
<span data-ttu-id="37c60-103">BizTalk Server vous permet de définir une liste de documents informatisés qui doivent toujours être inclus ou exclus lors du traitement d’un échange EDI.</span><span class="sxs-lookup"><span data-stu-id="37c60-103">BizTalk Server enables you to define a list of transaction sets that must always be included or excluded while processing an EDI interchange.</span></span> <span data-ttu-id="37c60-104">Cette section fournit des instructions sur la création de la liste des documents informatisés.</span><span class="sxs-lookup"><span data-stu-id="37c60-104">This section provides instructions on how to create the transaction set list.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="37c60-105">Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="37c60-105">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="37c60-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="37c60-106">Prerequisites</span></span>  
 <span data-ttu-id="37c60-107">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37c60-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-a-transaction-set-list"></a><span data-ttu-id="37c60-108">Pour configurer la liste des documents informatisés</span><span class="sxs-lookup"><span data-stu-id="37c60-108">To configure a transaction set list</span></span>  
  
1.  <span data-ttu-id="37c60-109">Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md).</span><span class="sxs-lookup"><span data-stu-id="37c60-109">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="37c60-110">Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="37c60-110">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="37c60-111">Sous l’onglet accord unidirectionnel, sous **paramètres des documents informatisés** , cliquez sur **liste des documents informatisés**.</span><span class="sxs-lookup"><span data-stu-id="37c60-111">On a one-way agreement tab, under **Transaction Set Settings** section, click **Transaction Set List**.</span></span>  
  
3.  <span data-ttu-id="37c60-112">Sélectionnez **prise en charge les documents informatisés de la liste** option si vous souhaitez créer une liste des documents informatisés qui doivent toujours être traités.</span><span class="sxs-lookup"><span data-stu-id="37c60-112">Select **Support Transaction Sets from the List** option if you want to create a list of transaction sets that must always be processed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="37c60-113">Utilisez cette option si vous recevez habituellement des échanges avec des types de transactions spécifiques, par exemple APERAK.</span><span class="sxs-lookup"><span data-stu-id="37c60-113">You would use this option if you typically receive interchanges with specific transaction types, say APERAK.</span></span> <span data-ttu-id="37c60-114">Dans ce cas, ajoutez ce type de transactions à la liste pour que les transactions des autres types ne soient pas traitées.</span><span class="sxs-lookup"><span data-stu-id="37c60-114">In that case, you add that transaction type to the list so that the transaction sets of other types are not processed at all.</span></span>  
  
4.  <span data-ttu-id="37c60-115">Sélectionnez **exclure les documents informatisés dans la liste** option si vous souhaitez créer une liste des documents informatisés qui ne doit pas être traité.</span><span class="sxs-lookup"><span data-stu-id="37c60-115">Select **Exclude Transaction Sets from the List** option if you want to create a list of transaction sets that must not be processed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="37c60-116">Utilisez cette option si vous recevez habituellement des échanges avec divers types de transactions.</span><span class="sxs-lookup"><span data-stu-id="37c60-116">You would use this option if you typically receive interchanges with varied transaction types.</span></span> <span data-ttu-id="37c60-117">Dans ce cas, vous ajoutez ces types de transactions à la liste pour laquelle vous n'obtenez aucun document informatisé.</span><span class="sxs-lookup"><span data-stu-id="37c60-117">In that case, you add those transaction type to the list for which you do not get any transaction sets.</span></span>  
  
5.  <span data-ttu-id="37c60-118">Cliquez sur la cellule vide dans le **UNH2.1** colonne et à partir de la liste déroulante, sélectionnez le type que vous souhaitez prendre en charge ou exclure informatisé.</span><span class="sxs-lookup"><span data-stu-id="37c60-118">Click the empty cell in the **UNH2.1** column and from the drop-down select the transaction set type you want to support on exclude.</span></span>  
  
6.  <span data-ttu-id="37c60-119">Pour supprimer un type de transaction dans la liste, sélectionnez la ligne pour le type de transaction, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="37c60-119">To delete a transaction type from the list, select the row for the transaction type, and click **Delete**.</span></span>  
  
7.  <span data-ttu-id="37c60-120">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="37c60-120">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c60-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37c60-121">See Also</span></span>  
 [<span data-ttu-id="37c60-122">Configuration des paramètres des documents informatisés (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="37c60-122">Configuring Transaction Set Settings (EDIFACT)</span></span>](../core/configuring-transaction-set-settings-edifact.md)