---
title: 'Étape 3 : Implémenter la connexion de l’adaptateur d’écho | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc223901-3ad3-4e71-8672-fea6bb4efe65
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a735654fd03f5efb39fe73eb845f4db3632d283
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="step-3-implement-the-connection-for-the-echo-adapter"></a><span data-ttu-id="ea4ef-102">Étape 3 : Implémenter la connexion de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="ea4ef-102">Step 3: Implement the Connection for the Echo Adapter</span></span>
<span data-ttu-id="ea4ef-103">![Étape 3 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-3of9.gif "Step_3of9")</span><span class="sxs-lookup"><span data-stu-id="ea4ef-103">![Step 3 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-3of9.gif "Step_3of9")</span></span>  
  
 <span data-ttu-id="ea4ef-104">**Durée :** 45 minutes</span><span class="sxs-lookup"><span data-stu-id="ea4ef-104">**Time to complete:** 45 minutes</span></span>  
  
 <span data-ttu-id="ea4ef-105">Dans cette étape, vous implémentez la capacité de connexion de la carte de l’écho.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-105">In this step, you implement the connection capability of the Echo adapter.</span></span> <span data-ttu-id="ea4ef-106">Conformément à la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], vous devez implémenter la classe abstraite suivant et les interfaces lors de la connexion au système cible.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-106">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], you must implement the following abstract class and interfaces when connecting to the target system.</span></span>  
  
-   `Microsoft.ServiceModel.Channels.Common.ConnectionUri`  
  
-   `Microsoft.ServiceModel.Channels.Common.IConnection`  
  
-   `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`  
  
 <span data-ttu-id="ea4ef-107">Au lieu de dériver à partir de la liste ci-dessus abstraite des classes et interfaces, les [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement les trois classes dérivées, EchoAdapterConnection, EchoAdapterConnectionUri et EchoAdapterConnectionFactory.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-107">Instead of deriving from the above abstract class and interfaces, the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates the three derived classes, EchoAdapterConnection, EchoAdapterConnectionUri, and EchoAdapterConnectionFactory.</span></span> <span data-ttu-id="ea4ef-108">En plus de la création des classes, chacune dispose d’une méthode par défaut qui lève une exception spécifique, `System.NotImplementedException`.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-108">In addition to creating the classes, each has a default method that throws a specific exception, `System.NotImplementedException`.</span></span>  <span data-ttu-id="ea4ef-109">Cette instruction rappelle au développeur d’implémenter chaque classe.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-109">This statement reminds the developer to implement each class.</span></span>  <span data-ttu-id="ea4ef-110">Lorsque la classe est implémentée, cette instruction de levée d’exceptions doit être supprimée.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-110">When the class is implemented, this exception-throwing statement must be removed.</span></span>  
  
 <span data-ttu-id="ea4ef-111">Dans la section suivante, vous mettez à jour ces trois classes pour mieux comprendre comment gérer une connexion, ce qui est la structure de l’URI et comment récupérer par programme des différents éléments de l’URI, puis utilisez ces éléments au sein de la carte.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-111">In the following section, you update those three classes to get a better understanding of how to handle a connection, what the URI structure is, and how to programmatically retrieve various URI elements and then use those elements within the adapter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ea4ef-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ea4ef-112">Prerequisites</span></span>  
 <span data-ttu-id="ea4ef-113">Avant de commencer cette étape, vous devez avoir terminé avec succès [étape 2 : classer l’adaptateur et les propriétés de connexion](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ea4ef-113">Before you begin this step, you must have successfully completed [Step 2: Categorize the Adapter and Connection Properties](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md).</span></span> <span data-ttu-id="ea4ef-114">Et vous devez avoir une vision claire de la `Microsoft.ServiceModel.Channels.Common.IConnection`, `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`, et `Microsoft.ServiceModel.Channels.Common.ConnectionUri` classes.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-114">And you should have a clear understanding of the `Microsoft.ServiceModel.Channels.Common.IConnection`, `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`, and `Microsoft.ServiceModel.Channels.Common.ConnectionUri` classes.</span></span>  
  
## <a name="connection-related-classes"></a><span data-ttu-id="ea4ef-115">Classes liées à la connexion</span><span class="sxs-lookup"><span data-stu-id="ea4ef-115">Connection-Related Classes</span></span>  
 <span data-ttu-id="ea4ef-116">Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère trois classes dérivées, EchoAdapterConnection, EchoAdapterConnectionUri et EchoAdapterConnectionFactory.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-116">The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] generates three derived classes, EchoAdapterConnection, EchoAdapterConnectionUri, and EchoAdapterConnectionFactory.</span></span> <span data-ttu-id="ea4ef-117">Les éléments suivants fournissent une vue d’ensemble des méthodes associées à chacun.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-117">The following provides a brief overview of methods associated with each.</span></span>  
  
### <a name="echoadapterconnection"></a><span data-ttu-id="ea4ef-118">EchoAdapterConnection</span><span class="sxs-lookup"><span data-stu-id="ea4ef-118">EchoAdapterConnection</span></span>  
 <span data-ttu-id="ea4ef-119">Selon la complexité de votre carte, vous devrez peut-être implémenter toutes les cinq méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-119">Depending on your adapter complexity, you might need to implement all of the following five methods.</span></span> <span data-ttu-id="ea4ef-120">Adaptateur d’écho, la plupart n'est pas prises en charge, car l’exemple d’adaptateur Echo n’implique pas de n’importe quel système cible.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-120">For Echo adapter, most are not supported, because the Echo adapter sample does not involve any target system.</span></span>  
  
|<span data-ttu-id="ea4ef-121">**Méthode**</span><span class="sxs-lookup"><span data-stu-id="ea4ef-121">**Method**</span></span>|<span data-ttu-id="ea4ef-122">**Description**</span><span class="sxs-lookup"><span data-stu-id="ea4ef-122">**Description**</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="ea4ef-123">Fermer void publique (délai d’expiration de l’intervalle de temps)</span><span class="sxs-lookup"><span data-stu-id="ea4ef-123">public void Close(TimeSpan timeout)</span></span>|<span data-ttu-id="ea4ef-124">Ferme la connexion au système cible.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-124">Closes the connection to the target system.</span></span> <span data-ttu-id="ea4ef-125">L’adaptateur d’écho utilise cette méthode pour ajouter uniquement des événements de trace à l’écouteur de trace.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-125">The Echo adapter uses this method to only add trace events to the trace listener.</span></span>|  
|<span data-ttu-id="ea4ef-126">public bool IsValid (délai d’expiration de l’intervalle de temps)</span><span class="sxs-lookup"><span data-stu-id="ea4ef-126">public bool IsValid(TimeSpan timeout)</span></span>|<span data-ttu-id="ea4ef-127">Retourne une valeur qui indique si la connexion est toujours valide.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-127">Returns a value indicating whether the connection is still valid.</span></span><br /><br /> <span data-ttu-id="ea4ef-128">Non pris en charge par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-128">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="ea4ef-129">Ouvrez void publique (délai d’expiration de l’intervalle de temps)</span><span class="sxs-lookup"><span data-stu-id="ea4ef-129">public void Open(TimeSpan timeout)</span></span>|<span data-ttu-id="ea4ef-130">Ouvre la connexion au système cible.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-130">Opens the connection to the target system.</span></span><br /><br /> <span data-ttu-id="ea4ef-131">Non applicable pour l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-131">N/A for the Echo adapter.</span></span> <span data-ttu-id="ea4ef-132">Toutefois, l’exemple montre comment utiliser un élément d’URI appelé enableAuthentication les utilisateurs à fournir un nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-132">However, the example shows you how to use a URI element called enableAuthentication to require users to provide a user name.</span></span>|  
|<span data-ttu-id="ea4ef-133">ClearContext() void publique</span><span class="sxs-lookup"><span data-stu-id="ea4ef-133">public void ClearContext()</span></span>|<span data-ttu-id="ea4ef-134">Efface le contexte de la connexion.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-134">Clears the context of the connection.</span></span> <span data-ttu-id="ea4ef-135">Cette méthode est appelée lorsque la connexion est redéfinie pour le pool de connexions.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-135">This method is called when the connection is set back to the connection pool.</span></span><br /><br /> <span data-ttu-id="ea4ef-136">Non pris en charge par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-136">Not supported by the Echo adapter.</span></span>|  
|<span data-ttu-id="ea4ef-137">Abort() void publique</span><span class="sxs-lookup"><span data-stu-id="ea4ef-137">public void Abort()</span></span>|<span data-ttu-id="ea4ef-138">Abandonne la connexion au système cible.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-138">Aborts the connection to the target system.</span></span><br /><br /> <span data-ttu-id="ea4ef-139">Non pris en charge par l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-139">Not supported by the Echo adapter.</span></span>|  
  
### <a name="echoadapterconnectionfactory"></a><span data-ttu-id="ea4ef-140">EchoAdapterConnectionFactory</span><span class="sxs-lookup"><span data-stu-id="ea4ef-140">EchoAdapterConnectionFactory</span></span>  
 <span data-ttu-id="ea4ef-141">La fabrique de connexion est responsable de la création de la connexion.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-141">The connection factory is responsible for creating the connection.</span></span> <span data-ttu-id="ea4ef-142">Par défaut, vous devez modifier cette classe uniquement lors de la connexion à un système cible.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-142">By default, you must modify this class only when connecting to a target system.</span></span> <span data-ttu-id="ea4ef-143">Bien que l’adaptateur Echo n’implique pas de n’importe quel système cible, il vous montre comment utiliser un élément URI personnalisé appelé enableAuthentication si votre connexion requiert une authentification utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-143">Although the Echo adapter does not involve any target system, it shows you how to use a custom URI element called enableAuthentication if your connection requires user authentication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea4ef-144">L’enableAuthentication n’est pas un mot clé, il est simplement un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-144">The enableAuthentication is not a keyword, it is just a variable name.</span></span> <span data-ttu-id="ea4ef-145">Par conséquent, vous pouvez choisir n’importe quel nom pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-145">Hence, you can choose any name for it.</span></span>  
  
### <a name="echoadapterconnectionuri"></a><span data-ttu-id="ea4ef-146">EchoAdapterConnectionUri</span><span class="sxs-lookup"><span data-stu-id="ea4ef-146">EchoAdapterConnectionUri</span></span>  
 <span data-ttu-id="ea4ef-147">Cela représente une chaîne de connexion au système cible.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-147">This represents a connection string to the target system.</span></span>  
  
|<span data-ttu-id="ea4ef-148">**Méthode**</span><span class="sxs-lookup"><span data-stu-id="ea4ef-148">**Method**</span></span>|<span data-ttu-id="ea4ef-149">**Description**</span><span class="sxs-lookup"><span data-stu-id="ea4ef-149">**Description**</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="ea4ef-150">substitution public Uri Uri</span><span class="sxs-lookup"><span data-stu-id="ea4ef-150">public override Uri Uri</span></span>|<span data-ttu-id="ea4ef-151">Obtient et définit l’Uri.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-151">Gets and sets the Uri.</span></span> <span data-ttu-id="ea4ef-152">Obtient générer la chaîne d’Uri et définit pour analyser la chaîne d’Uri.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-152">Gets to build the Uri string and sets to parse the Uri string.</span></span>|  
|<span data-ttu-id="ea4ef-153">public EchoAdapterConnectionUri()</span><span class="sxs-lookup"><span data-stu-id="ea4ef-153">public EchoAdapterConnectionUri()</span></span>|<span data-ttu-id="ea4ef-154">Initialise une nouvelle instance de la classe ConnectionUri.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-154">Initializes a new instance of the ConnectionUri class.</span></span>|  
|<span data-ttu-id="ea4ef-155">chaîne de substitution public SampleUriString</span><span class="sxs-lookup"><span data-stu-id="ea4ef-155">public override string SampleUriString</span></span>|<span data-ttu-id="ea4ef-156">Retourne EchoAdapter.SCHEME + » : //{hostname}/{application}?enableAuthentication={True&#124;False} ».</span><span class="sxs-lookup"><span data-stu-id="ea4ef-156">Returns EchoAdapter.SCHEME + "://{hostname}/{application}?enableAuthentication={True&#124;False}".</span></span><br /><br /> <span data-ttu-id="ea4ef-157">Cette chaîne de retour affiche en tant que le **exemple** dans les [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] d’outils, comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-157">This return string displays as the **Example** in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, as shown in the following figure.</span></span>|  
  
 <span data-ttu-id="ea4ef-158">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")</span><span class="sxs-lookup"><span data-stu-id="ea4ef-158">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")</span></span>  
  
## <a name="echo-adapter-connection-uri"></a><span data-ttu-id="ea4ef-159">URI de connexion de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="ea4ef-159">Echo Adapter Connection URI</span></span>  
 <span data-ttu-id="ea4ef-160">L’exemple de connexion de l’adaptateur Echo URI se présente comme suit : EchoAapter.SCHEME://{hostname}/{application}?enableAuthentication={true&#124;false}</span><span class="sxs-lookup"><span data-stu-id="ea4ef-160">The sample Echo adapter connection URI is described as: EchoAapter.SCHEME://{hostname}/{application}?enableAuthentication={true&#124;false}</span></span>  
  
 <span data-ttu-id="ea4ef-161">Le EchoAapter.SCHEME étant echov2, la connexion est :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-161">Since the EchoAapter.SCHEME is echov2, the connection URI is:</span></span>  
  
 <span data-ttu-id="ea4ef-162">echo2://lobhostname/lobapplication?enableAuthentication={true&#124;false}</span><span class="sxs-lookup"><span data-stu-id="ea4ef-162">echo2://lobhostname/lobapplication?enableAuthentication={true&#124;false}</span></span>  
  
 <span data-ttu-id="ea4ef-163">Vous pouvez lire l’URI de connexion précédente lorsque enableAuthentication = false comme suit :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-163">You can read the previous connection URI when enableAuthentication=false as follows:</span></span>  
  
 <span data-ttu-id="ea4ef-164">À l’aide du schéma de transport echov2, accédez à un ordinateur nommé lobhostname, où une application nommée lobapplication qui ne nécessite pas d’authentification est en attente pour votre connexion.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-164">Using the echov2 transport schema, go to a computer named lobhostname, where an application named lobapplication that does not require any authentication is waiting for your connection.</span></span>  
  
 <span data-ttu-id="ea4ef-165">Ou bien, lorsque enableAuthentication = true, la connexion comme suite :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-165">Or, when enableAuthentication=true, read the connection as follows:</span></span>  
  
 <span data-ttu-id="ea4ef-166">À l’aide du schéma de transport echov2, accédez à un ordinateur nommé lobhostname, où une application nommée lobapplication attend que l’authentification est en attente pour votre connexion.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-166">Using the echov2 transport schema, go to a computer named lobhostname, where an application named lobapplication expects that authentication is waiting for your connection.</span></span> <span data-ttu-id="ea4ef-167">Pour l’adaptateur d’écho uniquement un nom d’utilisateur est requis.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-167">For the Echo adapter, only a user name is required.</span></span>  
  
 <span data-ttu-id="ea4ef-168">Avec un URI défini, vous pouvez par programmation consommer et analyser pour la connectivité et de configuration.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-168">With a defined URI, you can programmatically consume and parse it for connectivity and configuration.</span></span> <span data-ttu-id="ea4ef-169">Si la connexion nécessite des données sensibles telles qu’un nom d’utilisateur et un mot de passe, ne contiennent pas ces informations dans l’URI.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-169">If the connection requires sensitive data such as a user name and password, do not contain such information in the URI.</span></span> <span data-ttu-id="ea4ef-170">Au lieu de cela, ajoutez ces informations dans le `System.ServiceModel.Description.ClientCredentials` objet.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-170">Instead, add such information in the `System.ServiceModel.Description.ClientCredentials` object.</span></span> <span data-ttu-id="ea4ef-171">L’exemple de code que vous ajoutez vous montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-171">The code example that you add shows you how to do so.</span></span>  
  
 <span data-ttu-id="ea4ef-172">Dans le code suivant, l’adaptateur Echo construit l’URI de deux façons pour vous expliquent comment l’adaptateur peut utiliser différents éléments de l’URI pour modifier la fonctionnalité de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-172">In the following code, the Echo adapter constructs the URI in two ways to show you how the adapter can use various URI elements to modify the adapter feature.</span></span>  
  
 <span data-ttu-id="ea4ef-173">echo2://lobhostname/lobapplication?enableAuthentication=[true&#124;false]</span><span class="sxs-lookup"><span data-stu-id="ea4ef-173">echo2://lobhostname/lobapplication?enableAuthentication=[true&#124;false]</span></span>  
  
 <span data-ttu-id="ea4ef-174">echo2://lobhostname/lobapplication?enableAuthentication=[true&#124;false]&echoInUpperCase=true</span><span class="sxs-lookup"><span data-stu-id="ea4ef-174">echo2://lobhostname/lobapplication?enableAuthentication=[true&#124;false]&echoInUpperCase=true</span></span>  
  
### <a name="retrieving-the-uri-element"></a><span data-ttu-id="ea4ef-175">La récupération de l’élément URI</span><span class="sxs-lookup"><span data-stu-id="ea4ef-175">Retrieving the URI Element</span></span>  
 <span data-ttu-id="ea4ef-176">Vous pouvez analyser chaque élément d’URI dans l’adaptateur d’écho URI echo2 : / lobhostname/lobapplication ? enableAuthentication = false & echoInUpperCase = false.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-176">You can parse each URI element in the Echo adapter URI echo2://lobhostname/lobapplication?enableAuthentication=false&echoInUpperCase=false.</span></span>  <span data-ttu-id="ea4ef-177">Les valeurs d’élément URI et les méthodes associées sont répertoriées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-177">The URI element values and associated methods are listed in the following table:</span></span>  
  
|<span data-ttu-id="ea4ef-178">**Valeur de l’élément URI**</span><span class="sxs-lookup"><span data-stu-id="ea4ef-178">**URI Element Value**</span></span>|<span data-ttu-id="ea4ef-179">**Méthode**</span><span class="sxs-lookup"><span data-stu-id="ea4ef-179">**Method**</span></span>|  
|---------------------------|----------------|  
|<span data-ttu-id="ea4ef-180">lobhostname</span><span class="sxs-lookup"><span data-stu-id="ea4ef-180">lobhostname</span></span>|<span data-ttu-id="ea4ef-181">`System.Uri.Host%2A` pour récupérer le nom d’hôte</span><span class="sxs-lookup"><span data-stu-id="ea4ef-181">`System.Uri.Host%2A` to retrieve the host name</span></span>|  
|<span data-ttu-id="ea4ef-182">Lobapplication</span><span class="sxs-lookup"><span data-stu-id="ea4ef-182">Lobapplication</span></span>|<span data-ttu-id="ea4ef-183">`System.Uri.AbsolutePath%2A` pour récupérer le nom de l’application cible</span><span class="sxs-lookup"><span data-stu-id="ea4ef-183">`System.Uri.AbsolutePath%2A` to retrieve the target application name</span></span>|  
|<span data-ttu-id="ea4ef-184">enableAuthentation=false</span><span class="sxs-lookup"><span data-stu-id="ea4ef-184">enableAuthentation=false</span></span>|<span data-ttu-id="ea4ef-185">GetQueryStringValue("enableAuthentication")</span><span class="sxs-lookup"><span data-stu-id="ea4ef-185">GetQueryStringValue("enableAuthentication")</span></span><br /><br /> <span data-ttu-id="ea4ef-186">Utilisez cet élément URI pour valider les informations d’identification utilisateur **Remarque :** GetQueryStringValue est une méthode statique définie dans le `Microsoft.ServiceModel.Channels.Common.ConnectionUri`</span><span class="sxs-lookup"><span data-stu-id="ea4ef-186">Use this URI element to validate user credentials **Note:**  GetQueryStringValue is a static method defined in the `Microsoft.ServiceModel.Channels.Common.ConnectionUri`</span></span>|  
|<span data-ttu-id="ea4ef-187">echoInUpperValue=false</span><span class="sxs-lookup"><span data-stu-id="ea4ef-187">echoInUpperValue=false</span></span>|<span data-ttu-id="ea4ef-188">GetQueryStringValue("echoInUpperValue")</span><span class="sxs-lookup"><span data-stu-id="ea4ef-188">GetQueryStringValue("echoInUpperValue")</span></span><br /><br /> <span data-ttu-id="ea4ef-189">Utilisez cet élément de l’URI à convertir la chaîne entrante en majuscules.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-189">Use this URI element to convert the incoming string to upper case.</span></span>|  
  
### <a name="enableauthentication-uri-element"></a><span data-ttu-id="ea4ef-190">Élément EnableAuthentication URI</span><span class="sxs-lookup"><span data-stu-id="ea4ef-190">EnableAuthentication URI Element</span></span>  
 <span data-ttu-id="ea4ef-191">Votre système cible souvent vous oblige à fournir des informations d’identification du client pour établir une connexion au système cible.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-191">Your target system often requires you to provide client credentials to establish a connection to the target system.</span></span> <span data-ttu-id="ea4ef-192">Comme indiqué, l’adaptateur Echo n’implique pas de n’importe quel système cible.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-192">As mentioned, the Echo adapter does not involve any target system.</span></span> <span data-ttu-id="ea4ef-193">Bien que sous forme d’exemple, il montre comment utiliser un élément URI personnalisé appelé enableAuthentication pour fournir les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-193">Though as a sample, it shows how to use a custom URI element called enableAuthentication to provide the credentials.</span></span>  
  
```  
 public class EchoAdapterConnection : IConnection   
{  
….  
   public void Open(TimeSpan timeout)  
  {  
    // only validate the credentials if EnableAuthentication  
    // connection property value is true  
    if (this.ConnectionFactory.ConnectionUri.EnableAuthentication)  
    {  
        // this adapter expects a value in username  
        if (this.connectionFactory.ClientCredentials != null &&  
            string.IsNullOrEmpty(this.connectionFactory.ClientCredentials.UserName.UserName))  
        {  
            throw new CredentialsException("Username is expected.");  
        }  
  }  
}  
```  
  
 <span data-ttu-id="ea4ef-194">Le code vérifie si enableAuthentication a la valeur true et si un nom d’utilisateur n’est pas fourni ; Si un nom d’utilisateur n’est pas fourni, il lève une exception, qui est interceptée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-194">The code checks to see if enableAuthentication is true and if a user name is not provided; if a user name is not provided, it throws an exception, which is caught by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, as shown below:</span></span>  
  
 <span data-ttu-id="ea4ef-195">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/901095c7-c70d-491a-a1ae-8f37f22a61a7.gif "901095c7-c70d-491a-a1ae-8f37f22a61a7")</span><span class="sxs-lookup"><span data-stu-id="ea4ef-195">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/901095c7-c70d-491a-a1ae-8f37f22a61a7.gif "901095c7-c70d-491a-a1ae-8f37f22a61a7")</span></span>  
  
 <span data-ttu-id="ea4ef-196">Pour fournir le nom d’utilisateur, vous pouvez l’entrer dans la boîte de dialogue Configurer l’adaptateur dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil, tel qu’indiqué dans l’illustration suivante :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-196">To provide the user name, you can enter it in the Configure Adapter dialog box in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] tool, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="ea4ef-197">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4069a7d-1403-4195-b0b5-21ad97dbc3ce.gif "e4069a7d-1403-4195-b0b5-21ad97dbc3ce")</span><span class="sxs-lookup"><span data-stu-id="ea4ef-197">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4069a7d-1403-4195-b0b5-21ad97dbc3ce.gif "e4069a7d-1403-4195-b0b5-21ad97dbc3ce")</span></span>  
  
### <a name="echoinuppercase-uri-element"></a><span data-ttu-id="ea4ef-198">Élément EchoInUpperCase URI</span><span class="sxs-lookup"><span data-stu-id="ea4ef-198">EchoInUpperCase URI Element</span></span>  
 <span data-ttu-id="ea4ef-199">L’élément EchoInUpperCase URI peut être référencé comme un indicateur booléen.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-199">The EchoInUpperCase URI element can be referenced like a Boolean flag.</span></span> <span data-ttu-id="ea4ef-200">Si l’indicateur est true, l’adaptateur convertit la chaîne d’entrée de l’opération EchoStrings en majuscules.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-200">If the flag is true, then the adapter converts the input string of the EchoStrings operation to uppercase.</span></span>  
  
 <span data-ttu-id="ea4ef-201">Pour modifier la valeur par défaut de l’élément d’URI echoInUpperCase, utilisez l’onglet Propriétés de l’URI de l’adaptateur à configurer dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], comme illustré ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-201">To change the default value of the echoInUpperCase URI element, use the URI Properties tab of the Configure Adapter in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], as shown below.</span></span>  
  
 <span data-ttu-id="ea4ef-202">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f22511b2-3fca-4875-ac65-8e61f4367e94.gif "f22511b2-3fca-4875-ac65-8e61f4367e94")</span><span class="sxs-lookup"><span data-stu-id="ea4ef-202">![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f22511b2-3fca-4875-ac65-8e61f4367e94.gif "f22511b2-3fca-4875-ac65-8e61f4367e94")</span></span>  
  
## <a name="updating-echoadapterconnection"></a><span data-ttu-id="ea4ef-203">Mise à jour EchoAdapterConnection</span><span class="sxs-lookup"><span data-stu-id="ea4ef-203">Updating EchoAdapterConnection</span></span>  
 <span data-ttu-id="ea4ef-204">Vous implémentez la méthode IsValid, Open et Close de la classe EchoAdapterConnection.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-204">You implement the IsValid, Open, and Close method of the EchoAdapterConnection class.</span></span>  
  
#### <a name="to-update-the-echoadapterconnection-class"></a><span data-ttu-id="ea4ef-205">Pour mettre à jour de la classe EchoAdapterConnection</span><span class="sxs-lookup"><span data-stu-id="ea4ef-205">To update the EchoAdapterConnection class</span></span>  
  
1.  <span data-ttu-id="ea4ef-206">Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterConnection.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-206">In **Solution Explorer**, double-click the **EchoAdapterConnection.cs** file.</span></span>  
  
2.  <span data-ttu-id="ea4ef-207">Dans l’éditeur Visual Studio, avec le bouton droit n’importe où dans l’éditeur, dans le menu contextuel, pointez sur **mode plan**, puis cliquez sur **arrêter le mode plan**.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-207">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="ea4ef-208">Dans l’éditeur Visual Studio, recherchez le **IsValid** (méthode).</span><span class="sxs-lookup"><span data-stu-id="ea4ef-208">In the Visual Studio editor, find the **IsValid** method.</span></span> <span data-ttu-id="ea4ef-209">À l’intérieur de la **IsValid** méthode, remplacez l’implémentation existante avec celui présenté ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-209">Inside the **IsValid** method, replace the existing implementation with the one below:</span></span>  
  
    ```csharp  
    return true;  
    ```  
  
4.  <span data-ttu-id="ea4ef-210">Dans l’éditeur Visual Studio, recherchez le **ouvrir** (méthode).</span><span class="sxs-lookup"><span data-stu-id="ea4ef-210">In the Visual Studio editor, find the **Open** method.</span></span> <span data-ttu-id="ea4ef-211">À l’intérieur de la **ouvrir** (méthode), remplacez l’implémentation existante avec l’implémentation suivante.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-211">Inside the **Open** method, replace the existing implementation with the following implementation.</span></span> <span data-ttu-id="ea4ef-212">Cet exemple montre comment utiliser l’élément d’enableAuthentication URI pour vérifier le nom d’utilisateur est fourni :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-212">This shows you how to use the URI enableAuthentication element to ensure user  name is provided:</span></span>  
  
    ```csharp  
    // only validate the credentials if EnableAuthentication  
    // connection property value is true  
    if (this.ConnectionFactory.ConnectionUri.EnableAuthentication)  
    {  
        // this adapter expects a value in username  
        // it just logs the credentials in the trace file  
        if (this.connectionFactory.ClientCredentials != null &&  
            string.IsNullOrEmpty(this.connectionFactory.ClientCredentials.UserName.UserName))  
        {  
            throw new CredentialsException("Username is expected.");  
        }  
        // got the username, log it in trace file  
        EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Username is " + this.connectionFactory.ClientCredentials.UserName.UserName);  
    }  
    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Connection successfully established!");  
    ```  
  
5.  <span data-ttu-id="ea4ef-213">Dans l’éditeur Visual Studio, recherchez le **fermer** (méthode).</span><span class="sxs-lookup"><span data-stu-id="ea4ef-213">In the Visual Studio editor, find the **Close** method.</span></span> <span data-ttu-id="ea4ef-214">À l’intérieur de la **fermer** (méthode), ajoutez l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-214">Inside the **Close** method, add the following single statement:</span></span>  
  
    ```csharp  
    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Close", "Connection successfully closed!");  
    ```  
  
## <a name="updating-the-echoadapterconnectionfactory"></a><span data-ttu-id="ea4ef-215">Mise à jour de la EchoAdapterConnectionFactory</span><span class="sxs-lookup"><span data-stu-id="ea4ef-215">Updating the EchoAdapterConnectionFactory</span></span>  
 <span data-ttu-id="ea4ef-216">Vous implémentez le constructeur de EchoAdapterConnectionFactory et que vous ajoutez deux propriétés appelées ClientCredentials et ConnectionUri.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-216">You implement EchoAdapterConnectionFactory constructor, and add two properties called ClientCredentials and ConnectionUri.</span></span>  
  
#### <a name="to-update-the-echoadapterconnectionfactory-class"></a><span data-ttu-id="ea4ef-217">Pour mettre à jour de la classe EchoAdapterConnectionFactory</span><span class="sxs-lookup"><span data-stu-id="ea4ef-217">To update the EchoAdapterConnectionFactory class</span></span>  
  
1.  <span data-ttu-id="ea4ef-218">Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterConnectionFactory.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-218">In **Solution Explorer**, double-click the **EchoAdapterConnectionFactory.cs** file.</span></span>  
  
2.  <span data-ttu-id="ea4ef-219">Dans l’éditeur Visual Studio, avec le bouton droit n’importe où dans l’éditeur, dans le menu contextuel, pointez sur **mode plan**, puis cliquez sur **arrêter le mode plan**.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-219">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="ea4ef-220">Dans l’éditeur Visual Studio, recherchez le **champs privés** région.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-220">In the Visual Studio editor, find the **Private Fields** region.</span></span> <span data-ttu-id="ea4ef-221">Ajoutez l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-221">Add the following single statement:</span></span>  
  
    ```csharp  
    private EchoAdapterConnectionUri connectionUri;  
    ```  
  
     <span data-ttu-id="ea4ef-222">La liste des champs privés doit correspondre à la suivante :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-222">Your list of private fields should match the following:</span></span>  
  
    ```csharp  
    // Stores the client credentials  
    private ClientCredentials clientCredentials;  
    // Stores the adapter class  
    private EchoAdapter adapter;  
    private EchoAdapterConnectionUri connectionUri;  
    ```  
  
4.  <span data-ttu-id="ea4ef-223">Dans l’éditeur Visual Studio, recherchez le **EchoAdapterConnectionFactory** (méthode).</span><span class="sxs-lookup"><span data-stu-id="ea4ef-223">In the Visual Studio editor, find the **EchoAdapterConnectionFactory** method.</span></span> <span data-ttu-id="ea4ef-224">À l’intérieur de la **EchoAdapterConnectionFactory** méthode de constructeur, avant «} », ajoutez l’instruction suivante en tant que la dernière instruction.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-224">Inside the **EchoAdapterConnectionFactory** constructor method, before "}", add the following single statement as the last statement.</span></span>  
  
    ```csharp  
    this.connectionUri = connectionUri as EchoAdapterConnectionUri;  
    ```  
  
     <span data-ttu-id="ea4ef-225">L’implémentation de la **EchoAdapterConnectionFactory** (méthode) doit correspondre à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-225">The implementation of the **EchoAdapterConnectionFactory** method should match the following:</span></span>  
  
    ```csharp  
    /// <summary>  
    /// Initializes a new instance of the EchoAdapterConnectionFactory class  
    /// </summary>  
    public EchoAdapterConnectionFactory(ConnectionUri connectionUri  
        , ClientCredentials clientCredentials  
        , EchoAdapter adapter)  
    {  
        this.clientCredentials = clientCredentials;  
        this.adapter = adapter;  
        //added  
        this.connectionUri = connectionUri as EchoAdapterConnectionUri;  
    }  
    ```  
  
5.  <span data-ttu-id="ea4ef-226">Dans l’éditeur Visual Studio, recherchez le **propriétés publiques** région.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-226">In the Visual Studio editor, find the **Public Properties** region.</span></span> <span data-ttu-id="ea4ef-227">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-227">Add the following code:</span></span>  
  
    ```csharp  
    /// <summary>  
    /// Returns the client credentials  
    /// </summary>  
    public ClientCredentials ClientCredentials  
    {  
        get  
        {  
            return this.clientCredentials;  
        }  
    }  
  
    /// <summary>  
    /// Returns the Connection Uri for this adapter  
    /// </summary>  
    public EchoAdapterConnectionUri ConnectionUri  
    {  
        get  
        {  
            return this.connectionUri;  
        }  
    }  
    ```  
  
## <a name="updating-the-echoadapterconnectionuri"></a><span data-ttu-id="ea4ef-228">Mise à jour de la EchoAdapterConnectionUri</span><span class="sxs-lookup"><span data-stu-id="ea4ef-228">Updating the EchoAdapterConnectionUri</span></span>  
 <span data-ttu-id="ea4ef-229">Vous implémentez le constructeur par défaut de EchoAdapterConnectionUri et EchoAdapterConnectionUri(Uri uri) surchargé constructeur public substituer la propriété Uri de l’Uri.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-229">You implement the EchoAdapterConnectionUri default constructor, EchoAdapterConnectionUri(Uri uri) overloaded constructor, and the public override Uri Uri property.</span></span>  
  
#### <a name="to-update-the-echoadapterconnectionuri-class"></a><span data-ttu-id="ea4ef-230">Pour mettre à jour de la classe EchoAdapterConnectionUri</span><span class="sxs-lookup"><span data-stu-id="ea4ef-230">To update the EchoAdapterConnectionUri class</span></span>  
  
1.  <span data-ttu-id="ea4ef-231">Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterConnectionUri.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-231">In **Solution Explorer**, double-click the **EchoAdapterConnectionUri.cs** file.</span></span>  
  
2.  <span data-ttu-id="ea4ef-232">Dans l’éditeur Visual Studio, avec le bouton droit n’importe où dans l’éditeur, dans le menu contextuel, pointez sur **mode plan**, puis cliquez sur **arrêter le mode plan**.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-232">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="ea4ef-233">Dans l’éditeur Visual Studio, recherchez le **constructeurs** région.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-233">In the Visual Studio editor, find the **Constructors** region.</span></span> <span data-ttu-id="ea4ef-234">À l’intérieur de la **EchoAdapterConnectionUri()** un constructeur par défaut, ajoutez l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-234">Inside the **EchoAdapterConnectionUri()** default constructor, add the following statement:</span></span>  
  
    ```csharp  
    Uri = new Uri("echov2://lobhostname/lobapplication?enableauthentication=False");  
    ```  
  
4.  <span data-ttu-id="ea4ef-235">Dans l’éditeur Visual Studio, à l’intérieur de la **EchoAdapterConnectionUri (Uri uri)** surchargées de constructeur et ajoutez l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-235">In the Visual Studio editor, inside the **EchoAdapterConnectionUri(Uri uri)** overloaded constructor, and add the following statement:</span></span>  
  
    ```csharp  
    Uri = uri;  
    ```  
  
     <span data-ttu-id="ea4ef-236">Votre implémentation de la méthode EchoAdapterConnectionUri(Uri uri) doit correspondre à la suivante :</span><span class="sxs-lookup"><span data-stu-id="ea4ef-236">Your implementation of the EchoAdapterConnectionUri(Uri uri) method should match the following:</span></span>  
  
    ```csharp  
    public EchoAdapterConnectionUri(Uri uri)  
        : base()  
    {  
        Uri = uri;  
    }  
    ```  
  
5.  <span data-ttu-id="ea4ef-237">Dans l’éditeur Visual Studio, à l’intérieur de la **public remplacer Uri Uri** (méthode), remplacer l’avec la logique suivante.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-237">In the Visual Studio editor, inside the **public override Uri Uri** method, replace the existing with the following logic.</span></span> <span data-ttu-id="ea4ef-238">La méthode get génère l’Uri avec echoInUpperCase ou sans lui.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-238">The get builds the Uri with echoInUpperCase or without it.</span></span> <span data-ttu-id="ea4ef-239">Le jeu d’analyse de l’URI pour récupérer le nom d’hôte, nom de la base de données et valeurs de requête.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-239">The set parses the URI to retrieve host name, database name, and query values.</span></span>  
  
    ```csharp  
    get  
    {  
        // Build the uri  
        if (String.IsNullOrEmpty(this.hostname)) throw new InvalidUriException("Invalid target system host name.");  
        if (String.IsNullOrEmpty(this.application)) throw new InvalidUriException("Invalid target system data source name.");  
        if (EchoInUpperCase)  
        {  
            // build the uri with echoInUpperCase= query string  
            return new Uri(EchoAdapter.SCHEME + "://" + Hostname + "/" + Application + "?" + "enableAuthentication=" + EnableAuthentication + "&" + "echoInUpperCase=" + echoInUpperCase);  
        }  
        else  
        {  
            // build the uri without echoInUpperCase= query string  
            return new Uri(EchoAdapter.SCHEME + "://" + Hostname + "/" + Application + "?" + "enableAuthentication=" + EnableAuthentication);  
        }  
    }  
    set  
    {  
        // Parse the uri  
        String[] enableAuthValue = GetQueryStringValue(value, "enableAuthentication");  
        if (enableAuthValue.Length > 0) this.enableAuthentication = Boolean.Parse(enableAuthValue[0]);  
        String[] echoInUpperValue = GetQueryStringValue(value, "echoInUpperCase");  
        if (echoInUpperValue.Length > 0) this.echoInUpperCase = Boolean.Parse(echoInUpperValue[0]);  
  
        this.hostname = value.Host;  
        String[] applicationValue = value.AbsolutePath.Split('/');  
        if (applicationValue.Length > 1) this.Application = applicationValue[1];  
    }  
    ```  
  
6.  <span data-ttu-id="ea4ef-240">Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-240">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
7.  <span data-ttu-id="ea4ef-241">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-241">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="ea4ef-242">Vous devez correctement compiler le projet.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-242">You should successfully compile the project.</span></span> <span data-ttu-id="ea4ef-243">Dans le cas contraire, vérifiez que vous avez suivi toutes les étapes ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-243">If not, ensure that you have followed every step above.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea4ef-244">Vous avez enregistré votre travail.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-244">You saved your work.</span></span> <span data-ttu-id="ea4ef-245">Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 4 : implémenter le Gestionnaire de parcourir des métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="ea4ef-245">You can safely close Visual Studio at this time or go to the next step, [Step 4: Implement the Metadata Browse Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="ea4ef-246">Quoi simplement ?</span><span class="sxs-lookup"><span data-stu-id="ea4ef-246">What Did I Just Do?</span></span>  
 <span data-ttu-id="ea4ef-247">Vous avez implémenté la connexion de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-247">You implemented the connection for the Echo adapter.</span></span> <span data-ttu-id="ea4ef-248">Vous avez appris les composants de connexion de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], la structure de base de l’URI de connexion, comment les éléments de l’URI d’analyser par programme et comment vous pouvez utiliser l’élément URI pour modifier la fonctionnalité de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-248">You learned the connection components of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], the basic structure of the connection URI, how to programmatically parse the URI elements, and how you can use the URI element to change the adapter feature.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ea4ef-249">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ea4ef-249">Next Steps</span></span>  
 <span data-ttu-id="ea4ef-250">Vous implémentez l’exploration des métadonnées, la recherche et la résolution de fonctionnalités et l’échange de messages sortants.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-250">You implement metadata browsing, searching, and resolving capabilities, and the outbound message exchange.</span></span> <span data-ttu-id="ea4ef-251">Enfin, vous générez et déployez l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ea4ef-251">Finally, you build and deploy the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4ef-252">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea4ef-252">See Also</span></span>  
 <span data-ttu-id="ea4ef-253">[Étape 4 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ea4ef-253">[Step 4: Implement the Metadata Browse Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="ea4ef-254">Didacticiel 1 : Développer l’adaptateur Echo</span><span class="sxs-lookup"><span data-stu-id="ea4ef-254">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)