---
title: "Réception de PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9acc71ec-05b8-4490-b3ba-0ce7f27a5a6a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cca87df1875f648abe2a986fb0d94b16865ee72f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="receiving-from-peoplesoft"></a><span data-ttu-id="a5f53-102">Réception à partir de PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="a5f53-102">Receiving from PeopleSoft</span></span>
<span data-ttu-id="a5f53-103">L'adaptateur Microsoft pour PeopleSoft Enterprise est un adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a5f53-103">The Microsoft Adapter for PeopleSoft Enterprise is a send adapter.</span></span> <span data-ttu-id="a5f53-104">Il prend en charge les échanges de type sollicitation-réponse et permet d'envoyer une requête et d'obtenir une réponse.</span><span class="sxs-lookup"><span data-stu-id="a5f53-104">The adapter supports solicit-response, so that you can send a query and get back a response.</span></span> <span data-ttu-id="a5f53-105">Cependant, si vous souhaitez seulement recevoir des données de PeopleSoft, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a5f53-105">However, if you want only to receive data from PeopleSoft, you must take two additional steps:</span></span>  
  
1.  <span data-ttu-id="a5f53-106">Créez un pipeline de réception personnalisé à l'aide du composant de pipeline Set Namespace.</span><span class="sxs-lookup"><span data-stu-id="a5f53-106">Create a custom receive pipeline using the Set Namespace pipeline component.</span></span>  
  
2.  <span data-ttu-id="a5f53-107">Créez un port de réception accessible à partir de PeopleSoft, tel qu'un port utilisant un adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5f53-107">Create a receive port accessible from PeopleSoft such as a port using the HTTP Adapter.</span></span> <span data-ttu-id="a5f53-108">Utilisez le pipeline de réception personnalisé avec le port de réception.</span><span class="sxs-lookup"><span data-stu-id="a5f53-108">Use the custom receive pipeline with the receive port.</span></span>  
  
## <a name="set-namespace-pipeline-component"></a><span data-ttu-id="a5f53-109">Composant de Pipeline de Namespace Set</span><span class="sxs-lookup"><span data-stu-id="a5f53-109">Set Namespace Pipeline Component</span></span>  
 <span data-ttu-id="a5f53-110">Les messages reçus de PeopleSoft n'incluent pas d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="a5f53-110">Messages received from PeopleSoft do not include namespaces.</span></span> <span data-ttu-id="a5f53-111">Le composant de pipeline Set Namespace permet d'ajouter un espace de noms à un message entrant.</span><span class="sxs-lookup"><span data-stu-id="a5f53-111">The Set Namespace pipeline component enables you to add a namespace to the incoming message.</span></span>  
  
 <span data-ttu-id="a5f53-112">L'emplacement par défaut de ce composant de pipeline est C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\Pipeline Component.</span><span class="sxs-lookup"><span data-stu-id="a5f53-112">The default location for the Set Namespace pipeline component is C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\Pipeline Component.</span></span> <span data-ttu-id="a5f53-113">Vous devez copier le composant Microsoft.BizTalk.Adapters.Pipeline.SetNSForMsg.dll vers le répertoire Composant de pipeline utilisé par BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a5f53-113">You need to copy the component, Microsoft.BizTalk.Adapters.Pipeline.SetNSForMsg.dll, to the Pipeline Component directory used by BizTalk.</span></span> <span data-ttu-id="a5f53-114">Vous devez également ajouter le composant à la boîte à outils de Visual Studio pour pouvoir l'utiliser dans le Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="a5f53-114">You also need to add the component to the Visual Studio Toolbox in order to use it in the Pipeline Designer.</span></span>  
  
 <span data-ttu-id="a5f53-115">Pour plus d’informations sur l’emplacement d’installation du composant, consultez [déploiement des composants de Pipeline](../core/deploying-pipeline-components.md).</span><span class="sxs-lookup"><span data-stu-id="a5f53-115">For information about where to install the component, see [Deploying Pipeline Components](../core/deploying-pipeline-components.md).</span></span>  
  
 <span data-ttu-id="a5f53-116">Pour plus d’informations sur l’ajout du composant à la boîte à outils Visual Studio, consultez [l’utilisation de la boîte à outils](../core/how-to-use-the-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="a5f53-116">For information about adding the component to the Visual Studio Toolbox, see [How to Use the Toolbox](../core/how-to-use-the-toolbox.md).</span></span>  
  
## <a name="configure-the-set-namespace-pipeline-component"></a><span data-ttu-id="a5f53-117">Configurer le composant de Pipeline de Namespace de jeu</span><span class="sxs-lookup"><span data-stu-id="a5f53-117">Configure the Set Namespace Pipeline Component</span></span>  
 <span data-ttu-id="a5f53-118">Vous pouvez définir deux propriétés pour ce composant :</span><span class="sxs-lookup"><span data-stu-id="a5f53-118">The Set Namespace pipeline component has two properties you can set:</span></span>  
  
|<span data-ttu-id="a5f53-119">Utiliser</span><span class="sxs-lookup"><span data-stu-id="a5f53-119">Use this</span></span>|<span data-ttu-id="a5f53-120">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="a5f53-120">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="a5f53-121">**Par défaut Target Namespace**</span><span class="sxs-lookup"><span data-stu-id="a5f53-121">**Default Target Namespace**</span></span>|<span data-ttu-id="a5f53-122">Placer un espace de noms fixe dans le message entrant.</span><span class="sxs-lookup"><span data-stu-id="a5f53-122">Put a fixed namespace in the incoming message.</span></span>|  
|<span data-ttu-id="a5f53-123">**Target Namespace XPath**</span><span class="sxs-lookup"><span data-stu-id="a5f53-123">**Target Namespace XPath**</span></span>|<span data-ttu-id="a5f53-124">Extraire l'espace de noms du message entrant à partir de l'emplacement spécifié par XPath.</span><span class="sxs-lookup"><span data-stu-id="a5f53-124">Extract the namespace from the incoming message taking it from the location specified by the XPath.</span></span> <span data-ttu-id="a5f53-125">Si le composant ne trouve aucun espace de noms valide, il consigne un avertissement dans le journal des événements de l'application et il utilise l'espace de noms cible par défaut, si ce dernier est spécifié.</span><span class="sxs-lookup"><span data-stu-id="a5f53-125">If the component does not find a valid namespace, it logs a warning in the Application Event Log and, if it is specified, uses the Default Target Namespace.</span></span>|  
  
 <span data-ttu-id="a5f53-126">Si vous laissez ces deux propriétés vides, le composant n'affecte aucun espace de noms aux messages entrants mais consigne des avertissements dans le journal des événements de l'application.</span><span class="sxs-lookup"><span data-stu-id="a5f53-126">If you leave both properties blank, the component does not assign namespaces to incoming messages but does write warnings to the Application Event Log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f53-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5f53-127">See Also</span></span>  
 [<span data-ttu-id="a5f53-128">Développement d’applications</span><span class="sxs-lookup"><span data-stu-id="a5f53-128">Developing Applications</span></span>](../core/developing-applications4.md)