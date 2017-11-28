---
title: "Comment créer une Continuation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities, relating events
- tracking profiles, relating events
- continuations, tracking profiles
- activities, continuations
- events, relating
- orchestrations, business events
- tracking profiles, updating
- activities, tracking profiles
- tracking profiles, continuations
- tracking profiles, connecting activities
ms.assetid: 31d6fc24-676e-418c-8e78-1a46b045905d
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e63983b290f0f4d7dff544cd2faea45f6cf46adc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-continuation"></a><span data-ttu-id="e61da-102">Création d'une continuation</span><span class="sxs-lookup"><span data-stu-id="e61da-102">How to Create a Continuation</span></span>
<span data-ttu-id="e61da-103">Créez des continuations pour indiquer les événements commerciaux associés dans une ou plusieurs orchestrations. Pour cela, construisez des activités connectées.</span><span class="sxs-lookup"><span data-stu-id="e61da-103">You create continuations to indicate which business events in one or more orchestrations are related by constructing connected activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e61da-104">La mise à jour d'un modèle de suivi peut avoir des conséquences sur les instances d'activité en cours si l'activité comprend une continuation d'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="e61da-104">Updating a tracking profile can impact activity instances in progress if the activity includes a BAM continuation.</span></span> <span data-ttu-id="e61da-105">Notamment, si la mise à jour du modèle de suivi indique une interception en aval des données pour un élément d'activité déjà enregistré, il est possible que la valeur d'origine soit remplacée.</span><span class="sxs-lookup"><span data-stu-id="e61da-105">Specifically, if the update to the tracking profile specifies a downstream interception of data for an activity item already recorded, it is possible that the original value will be overwritten.</span></span> <span data-ttu-id="e61da-106">Par définition, un flux d'événements unique ne sera pas affecté par les mises à jour du modèle de suivi, car chaque objet de flux est lié à la version du modèle en place au moment où l'activité ou le flux a démarré.</span><span class="sxs-lookup"><span data-stu-id="e61da-106">In essence, any single event stream will not be affected by the application of tracking profile updates because each stream object is tied to the specific version of the profile which was in place at the time the activity/stream started.</span></span>  <span data-ttu-id="e61da-107">Cependant, les continuations étant le moyen de mettre en corrélation plusieurs flux d'événements, les flux n'ayant pas encore été lancés au moment de la mise à jour du modèle récupèrent les modifications dans la mise à jour. Il existe alors un risque pour les données d'être remplacées, comme décrit plus haut.</span><span class="sxs-lookup"><span data-stu-id="e61da-107">However, because continuations are the means of correlating multiple event streams, streams not yet begun at the time of a profile update will pick up the changes in the update, thus introducing the possible data overwrite described.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e61da-108">Vous pouvez créer des continuations avec des orchestrations qui ne traitent pas les messages.</span><span class="sxs-lookup"><span data-stu-id="e61da-108">You can create continuations with orchestrations that do not process messages.</span></span> <span data-ttu-id="e61da-109">Pour cela, obtenez la même fonctionnalité que pour les orchestrations qui traitent des messages en faisant passer des paramètres dans des appels d'exécution entre les orchestrations et en utilisant les API de l'analyse BAM pour traiter la continuation.</span><span class="sxs-lookup"><span data-stu-id="e61da-109">You can obtain the same functionality as you can for orchestrations that do process messages by passing parameters in execution calls between orchestrations and by using BAM APIs to process the continuation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e61da-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e61da-110">Prerequisites</span></span>  
 <span data-ttu-id="e61da-111">Pour effectuer la procédure suivante, vous devez avoir déployé les définitions d'activité BAM et les orchestrations que vous allez connecter.</span><span class="sxs-lookup"><span data-stu-id="e61da-111">To perform this procedure, you must have deployed BAM activity definitions and orchestrations that you will connect to.</span></span>  
  
### <a name="to-create-a-continuation"></a><span data-ttu-id="e61da-112">Pour créer une continuation</span><span class="sxs-lookup"><span data-stu-id="e61da-112">To create a continuation</span></span>  
  
1.  <span data-ttu-id="e61da-113">Ouvrir un modèle de suivi existant ou créer un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="e61da-113">Open an existing tracking profile or create a tracking profile.</span></span> <span data-ttu-id="e61da-114">Pour plus d’informations sur la création d’un modèle de suivi, consultez [comment créer un modèle de suivi](../core/how-to-create-a-tracking-profile.md).</span><span class="sxs-lookup"><span data-stu-id="e61da-114">For information about creating a tracking profile, see [How to Create a Tracking Profile](../core/how-to-create-a-tracking-profile.md).</span></span>  
  
2.  <span data-ttu-id="e61da-115">Identifier un *le jeton de continuation,* qui est un élément d’information unique qui est disponible pour les deux activités.</span><span class="sxs-lookup"><span data-stu-id="e61da-115">Identify a *continuation token,* which is a piece of unique information that is available to both activities.</span></span> <span data-ttu-id="e61da-116">Par exemple, si un **CreditHistory** activité est activée par un message envoyé à partir d’un **LoanProcess** activité au sein d’un **EquityLoan**d’orchestration, le champ SSN de le message peut être utilisé comme un jeton de liaison, car il est courant pour les deux activités.</span><span class="sxs-lookup"><span data-stu-id="e61da-116">For example, if a **CreditHistory** activity is activated by a message sent from a **LoanProcess** activity within an **EquityLoan**orchestration, the SSN field of the message can be used as a continuation token because it is common to both activities.</span></span>  
  
3.  <span data-ttu-id="e61da-117">Cliquez sur l’activité, puis sélectionnez **Nouvelle Continuation** pour créer une continuation (CreditHistory).</span><span class="sxs-lookup"><span data-stu-id="e61da-117">Right-click the activity and then select **New Continuation** to create a continuation (CreditHistory).</span></span> <span data-ttu-id="e61da-118">Nommez le nœud de continuation que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="e61da-118">Name the continuation node you just created.</span></span>  
  
4.  <span data-ttu-id="e61da-119">Dans la vue de planification d'orchestration, copiez le jeton de continuation que vous avez choisi à l'étape 2 (dans le cas présent, le numéro SSN de l'action Envoi) et collez-le dans le nœud de continuation que vous avez créé à l'étape 3.</span><span class="sxs-lookup"><span data-stu-id="e61da-119">From the Orchestration Schedule View, select the continuation token you chose in step 2, such as SSN (in this case from the Send action) and drop it into the continuation node you created in step 3.</span></span>  
  
5.  <span data-ttu-id="e61da-120">Cliquez sur l’activité et sélectionnez **nouveau ContinuationID** pour créer un nœud Continuationid.</span><span class="sxs-lookup"><span data-stu-id="e61da-120">Right-click the activity and select **New ContinuationID** to create a Continuation ID node.</span></span> <span data-ttu-id="e61da-121">Nommez-le en utilisant le nom que vous avez choisi à l'étape 3 et déposez-le sur le nœud contenant les éléments de données correspondants (dans le cas présent, le numéro SSN de l'action Réception).</span><span class="sxs-lookup"><span data-stu-id="e61da-121">Name it using the name you chose in step 3, and drop it in the node that contains the corresponding data item (in this case, SSN from the Receive action).</span></span>  
  
6.  <span data-ttu-id="e61da-122">Sur le **fichier**menu, cliquez sur **Enregistrer sous**enregistrer le modèle de suivi sous la forme d’un fichier .btt à la base de données de gestion BizTalk et pour éviter de remplacer tout fichier .btt existant.</span><span class="sxs-lookup"><span data-stu-id="e61da-122">On the **File**menu, click **Save As**to save the tracking profile as a .btt file to the BizTalk Management database and to avoid overwriting any existing .btt file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61da-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e61da-123">See Also</span></span>  
 <span data-ttu-id="e61da-124">[Nœuds continuation et ContinuationID](../core/continuation-and-continuationid-nodes.md) </span><span class="sxs-lookup"><span data-stu-id="e61da-124">[Continuation and ContinuationID Nodes](../core/continuation-and-continuationid-nodes.md) </span></span>  
 [<span data-ttu-id="e61da-125">Création de modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="e61da-125">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)