---
title: "Configuration des documents informatisés liste (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f277318-90e9-4ad3-843a-e6128837fa2b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18b11ea09c7c3156aea18b95d758228e55994901
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-transaction-set-list-x12"></a><span data-ttu-id="020c9-102">Configuration de la liste des documents informatisés (X12)</span><span class="sxs-lookup"><span data-stu-id="020c9-102">Configuring Transaction Set List (X12)</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="020c9-103"> permet de définir la liste des documents informatisés qui doivent toujours être inclus ou exclus lors du traitement d'un échange EDI.</span><span class="sxs-lookup"><span data-stu-id="020c9-103"> enables you to define a list of transaction sets that must always be included or excluded while processing an EDI interchange.</span></span> <span data-ttu-id="020c9-104">Cette section fournit des instructions sur la création de la liste des documents informatisés.</span><span class="sxs-lookup"><span data-stu-id="020c9-104">This section provides instructions on how to create the transaction set list.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="020c9-105">Les paramètres décrits dans cette rubrique s'appliquent également aux échanges HIPAA.</span><span class="sxs-lookup"><span data-stu-id="020c9-105">The settings described here also apply to HIPAA interchanges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="020c9-106">Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="020c9-106">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="020c9-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="020c9-107">Prerequisites</span></span>  
 <span data-ttu-id="020c9-108">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="020c9-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-a-transaction-set-list"></a><span data-ttu-id="020c9-109">Pour configurer la liste des documents informatisés</span><span class="sxs-lookup"><span data-stu-id="020c9-109">To configure a transaction set list</span></span>  
  
1.  <span data-ttu-id="020c9-110">Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md).</span><span class="sxs-lookup"><span data-stu-id="020c9-110">Create an X12 encoding agreement as described in [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span> <span data-ttu-id="020c9-111">Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="020c9-111">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="020c9-112">Sous l’onglet accord unidirectionnel, sous **paramètres des documents informatisés** , cliquez sur **liste des documents informatisés**.</span><span class="sxs-lookup"><span data-stu-id="020c9-112">On a one-way agreement tab, under **Transaction Set Settings** section, click **Transaction Set List**.</span></span>  
  
3.  <span data-ttu-id="020c9-113">Sélectionnez **prise en charge les documents informatisés de la liste** option si vous souhaitez créer une liste des documents informatisés qui doivent toujours être traités.</span><span class="sxs-lookup"><span data-stu-id="020c9-113">Select **Support Transaction Sets from the List** option if you want to create a list of transaction sets that must always be processed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="020c9-114">Utilisez cette option si vous recevez habituellement des échanges avec des types de transactions spécifiques, par exemple 850.</span><span class="sxs-lookup"><span data-stu-id="020c9-114">You would use this option if you typically receive interchanges with specific transaction types, say 850.</span></span> <span data-ttu-id="020c9-115">Dans ce cas, ajoutez ce type de transactions à la liste pour que les transactions des autres types ne soient pas traitées.</span><span class="sxs-lookup"><span data-stu-id="020c9-115">In that case, you add that transaction type to the list so that the transaction sets of other types are not processed at all.</span></span>  
  
4.  <span data-ttu-id="020c9-116">Sélectionnez **exclure les documents informatisés dans la liste** option si vous souhaitez créer une liste des documents informatisés qui ne doit pas être traité.</span><span class="sxs-lookup"><span data-stu-id="020c9-116">Select **Exclude Transaction Sets from the List** option if you want to create a list of transaction sets that must not be processed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="020c9-117">Utilisez cette option si vous recevez habituellement des échanges avec divers types de transactions.</span><span class="sxs-lookup"><span data-stu-id="020c9-117">You would use this option if you typically receive interchanges with varied transaction types.</span></span> <span data-ttu-id="020c9-118">Dans ce cas, vous ajoutez ces types de transactions à la liste pour laquelle vous n'obtenez aucun document informatisé.</span><span class="sxs-lookup"><span data-stu-id="020c9-118">In that case, you add those transaction type to the list for which you do not get any transaction sets.</span></span>  
  
5.  <span data-ttu-id="020c9-119">Cliquez sur la cellule vide dans le **ST01** colonne et à partir de la liste déroulante, sélectionnez le type que vous souhaitez prendre en charge ou exclure informatisé.</span><span class="sxs-lookup"><span data-stu-id="020c9-119">Click the empty cell in the **ST01** column and from the drop-down select the transaction set type you want to support on exclude.</span></span>  
  
6.  <span data-ttu-id="020c9-120">Pour supprimer un type de transaction dans la liste, sélectionnez la ligne pour le type de transaction, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="020c9-120">To delete a transaction type from the list, select the row for the transaction type, and click **Delete**.</span></span>  
  
7.  <span data-ttu-id="020c9-121">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="020c9-121">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="020c9-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="020c9-122">See Also</span></span>  
 [<span data-ttu-id="020c9-123">Configuration des paramètres (X12) documents informatisés</span><span class="sxs-lookup"><span data-stu-id="020c9-123">Configuring Transaction Set Settings (X12)</span></span>](../core/configuring-transaction-set-settings-x12.md)