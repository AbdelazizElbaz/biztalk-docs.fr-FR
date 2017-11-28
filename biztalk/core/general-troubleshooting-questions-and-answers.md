---
title: "Dépannage de Questions et réponses | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2f89d92-0a97-4017-8b8e-6afd8b20eaf4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37e63f8838dea7adee91b5b43b2bc881cb53eae1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="general-troubleshooting-questions-and-answers"></a><span data-ttu-id="6bf59-102">Questions et réponses d'ordre général sur le dépannage</span><span class="sxs-lookup"><span data-stu-id="6bf59-102">General Troubleshooting Questions and Answers</span></span>
<span data-ttu-id="6bf59-103">Les questions/réponses de cette rubrique vous aideront à résoudre les problèmes que vous pouvez rencontrer avec le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6bf59-103">This topic has questions and answers to help you resolve issues with the BizTalk Mapper.</span></span>  
  
## <a name="how-do-i-specify-xslt-output-settings"></a><span data-ttu-id="6bf59-104">Comment spécifier les paramètres de sortie XSLT ?</span><span class="sxs-lookup"><span data-stu-id="6bf59-104">How do I specify XSLT output settings?</span></span>  
 <span data-ttu-id="6bf59-105">Vous pouvez utiliser le Mappeur BizTalk pour incluent ou ignorent les déclarations XML et contrôler l’encodage utilisé pour les données d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="6bf59-105">You can use the BizTalk Mapper to include or omit XML declarations, and control the encoding used for output instance data.</span></span>  
  
#### <a name="include-or-exclude-an-xml-declaration"></a><span data-ttu-id="6bf59-106">Inclure ou exclure une déclaration XML</span><span class="sxs-lookup"><span data-stu-id="6bf59-106">Include or exclude an XML declaration</span></span>  
  
1.  <span data-ttu-id="6bf59-107">Dans la vue Grille, cliquez sur la grille du Mappeur.</span><span class="sxs-lookup"><span data-stu-id="6bf59-107">In the Grid view, click the mapper grid.</span></span> <span data-ttu-id="6bf59-108">Le **propriétés** fenêtre affiche les propriétés de la grille.</span><span class="sxs-lookup"><span data-stu-id="6bf59-108">The **Properties** window displays the grid properties.</span></span>  
  
2.  <span data-ttu-id="6bf59-109">Dans la liste déroulante pour le **omettre la déclaration XML** propriété, sélectionnez **Oui** pour omettre une déclaration XML, ou sélectionnez **non** pour ne pas omettre une déclaration XML.</span><span class="sxs-lookup"><span data-stu-id="6bf59-109">In the drop-down list for the **Omit XML Declaration** property, select **Yes** to omit an XML declaration, or select **No** not to omit an XML declaration.</span></span>  
  
#### <a name="set-encoding-for-output-instance-data"></a><span data-ttu-id="6bf59-110">Définir le codage de données d’instance de sortie</span><span class="sxs-lookup"><span data-stu-id="6bf59-110">Set encoding for output instance data</span></span>  
  
1.  <span data-ttu-id="6bf59-111">Dans la vue Grille, cliquez sur la grille du Mappeur.</span><span class="sxs-lookup"><span data-stu-id="6bf59-111">In the Grid view, click the mapper grid.</span></span> <span data-ttu-id="6bf59-112">Le **propriétés** fenêtre affiche les propriétés de la grille.</span><span class="sxs-lookup"><span data-stu-id="6bf59-112">The **Properties** window displays the grid properties.</span></span>  
  
2.  <span data-ttu-id="6bf59-113">Dans la liste déroulante pour le **codage XSLT** propriété, sélectionnez le jeu de caractères vous souhaitez utiliser pour les données d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="6bf59-113">In the drop-down list for the **XSLT Encoding** property, select the character set you want to use for the output instance data.</span></span>  
  
## <a name="how-do-i-create-multipart-mappings"></a><span data-ttu-id="6bf59-114">Comment créer des mappages à parties multiples ?</span><span class="sxs-lookup"><span data-stu-id="6bf59-114">How do I create multipart mappings?</span></span>  
 <span data-ttu-id="6bf59-115">Si vous avez plusieurs mappages sont utilisés ensemble, vous devez les associer dans une orchestration à l’aide de la **transformer** forme pour les tester ensemble.</span><span class="sxs-lookup"><span data-stu-id="6bf59-115">If you have multiple maps that are used together, you will need to combine them in an orchestration by using the **Transform** shape to test them together.</span></span> <span data-ttu-id="6bf59-116">Le Mappeur BizTalk ne peut tester qu'un seul mappage à la fois.</span><span class="sxs-lookup"><span data-stu-id="6bf59-116">The BizTalk Mapper can test only one map at a time.</span></span>  
  
## <a name="why-isnt-my-database-functoid-working"></a><span data-ttu-id="6bf59-117">Le fonctoid de base de données ne fonctionne pas. Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="6bf59-117">Why isn't my database functoid working?</span></span>  
 <span data-ttu-id="6bf59-118">Les fonctoids de base de données **recherche de base de données** et **extracteur de valeur** ne retournent pas directement les informations sur les erreurs au lieu de cela, de capturer les informations et de fournir à la **retourd’erreur** fonctoid pour une utilisation par votre carte.</span><span class="sxs-lookup"><span data-stu-id="6bf59-118">The database functoids **Database Lookup** and **Value Extractor** do not directly return error information; rather, they capture the information and supply it to the **Error Return** functoid for use by your map.</span></span> <span data-ttu-id="6bf59-119">Vous pouvez utiliser la **retour d’erreur** fonctoid pour la détection d’erreur dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="6bf59-119">You can use the **Error Return** functoid for error detection as in the following scenarios:</span></span>  
  
-   <span data-ttu-id="6bf59-120">Lorsque votre mappage comporte un **recherche de base de données** ou **extracteur de valeur** fonctoid qui se comporte pas comme prévu.</span><span class="sxs-lookup"><span data-stu-id="6bf59-120">When your map has a **Database Lookup** or **Value Extractor** functoid that is not behaving as expected.</span></span> <span data-ttu-id="6bf59-121">Pour afficher le message d'erreur, mappez temporairement le fonctoid à un champ du schéma de sortie.</span><span class="sxs-lookup"><span data-stu-id="6bf59-121">To see the error message, temporarily map the functoid to a field in the output schema.</span></span>  
  
-   <span data-ttu-id="6bf59-122">Si votre application attend un contenu de message différent lors de l'échec des opérations de la base de données.</span><span class="sxs-lookup"><span data-stu-id="6bf59-122">If your application expects different message content when database operations fail.</span></span> <span data-ttu-id="6bf59-123">Vous pouvez utiliser la **retour d’erreur** fonctoid pour détecter une erreur et mapper le message d’erreur à une autre structure pour que les applications en aval puissent réagir de manière contrôlée.</span><span class="sxs-lookup"><span data-stu-id="6bf59-123">You can use the **Error Return** functoid to detect an error and map the error message to an alternate structure so that downstream applications can react in a controlled manner.</span></span>  
  
 <span data-ttu-id="6bf59-124">Pour éviter les erreurs soient détectées qu’au moment de l’exécution, assurez-vous que le premier paramètre de la **retour d’erreur** fonctoid est le résultat d’une **recherche de base de données** fonctoid et non de la sortie d’un autre fonctoid dans la Catégorie de la base de données.</span><span class="sxs-lookup"><span data-stu-id="6bf59-124">To avoid errors that are detected only at run time, make sure that the first parameter to the **Error Return** functoid is the output of a **Database Lookup** functoid and not the output of any other functoid in the Database category.</span></span>  
  
 <span data-ttu-id="6bf59-125">Pour plus d’informations sur l’utilisation de la **retour d’erreur** fonctoid (y compris un exemple), consultez le **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="6bf59-125">For more information about using the **Error Return** functoid (including a sample), see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="why-is-my-map-failing-when-calling-my-custom-functoid"></a><span data-ttu-id="6bf59-126">Mon mappage ne parvient pas à appeler un fonctoid personnalisé. Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="6bf59-126">Why is my map failing when calling my custom functoid?</span></span>  
 <span data-ttu-id="6bf59-127">Vous devez installer les fonctoids personnalisés dans le GAC (Global Assembly Cache) sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour qu'un mappage puisse les appeler.</span><span class="sxs-lookup"><span data-stu-id="6bf59-127">Custom functoids must be installed into the global assembly cache (GAC) on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer before they can be invoked by a map.</span></span> <span data-ttu-id="6bf59-128">Vérifiez que l'assembly contenant votre fonctoid personnalisé a bien été signé et placé dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="6bf59-128">Verify that the assembly containing your custom functoid has been signed and placed into the GAC.</span></span> <span data-ttu-id="6bf59-129">Copiez également l'assembly dans le dossier « %BTSINSTALLPATH%\Developer Tools\Mapper Extensions ».</span><span class="sxs-lookup"><span data-stu-id="6bf59-129">Also, copy the assembly into the folder “%BTSINSTALLPATH%\Developer Tools\Mapper Extensions”.</span></span>  
  
 <span data-ttu-id="6bf59-130">Pour plus d’informations sur l’installation des assemblys dans le GAC, consultez [Installation de l’Assembly dans le GAC](../core/assembly-installation-in-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="6bf59-130">For more information about installing assemblies to the GAC, see [Assembly Installation in the GAC](../core/assembly-installation-in-the-gac.md).</span></span> <span data-ttu-id="6bf59-131">Pour afficher les assemblys installés dans le GAC, ouvrez le dossier des assemblys du répertoire d'installation de votre [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6bf59-131">To view assemblies installed in the GAC, navigate to the Assembly directory of your [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] installation directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf59-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bf59-132">See Also</span></span>  
 [<span data-ttu-id="6bf59-133">Résolution des problèmes de mappages</span><span class="sxs-lookup"><span data-stu-id="6bf59-133">Troubleshooting Maps</span></span>](../core/troubleshooting-maps.md)