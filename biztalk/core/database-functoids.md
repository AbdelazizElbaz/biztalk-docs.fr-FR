---
title: "Fonctoids de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77bc9390-cdb5-42ff-8b28-6265c51c79fc
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63a719299ef6678b9fd38a936d84ba9b1f57a85b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="database-functoids"></a><span data-ttu-id="a7562-102">Fonctoids de base de données</span><span class="sxs-lookup"><span data-stu-id="a7562-102">Database Functoids</span></span>
<span data-ttu-id="a7562-103">**Base de données** fonctoids extraient des données à partir d’une base de données pour une utilisation dans un message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="a7562-103">**Database** functoids extract data from a database for use in an output instance message.</span></span> 

## <a name="overview"></a><span data-ttu-id="a7562-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="a7562-104">Overview</span></span>
<span data-ttu-id="a7562-105">Voici une liste de la **base de données** fonctoids et comment vous pouvez les utiliser :</span><span class="sxs-lookup"><span data-stu-id="a7562-105">The following is a list of the **Database** functoids and how you can use them:</span></span>  
  
-   <span data-ttu-id="a7562-106">**Recherche de la base de données.**</span><span class="sxs-lookup"><span data-stu-id="a7562-106">**Database Lookup.**</span></span> <span data-ttu-id="a7562-107">Utilisez le **recherche de base de données** fonctoid pour extraire des informations à partir d’une base de données et les stocker en tant qu’un jeu d’enregistrements Microsoft ActiveX Data Objects .NET (ADO.NET).</span><span class="sxs-lookup"><span data-stu-id="a7562-107">Use the **Database Lookup** functoid to extract information from a database and store it as a Microsoft ActiveX Data Objects .NET (ADO.NET) recordset.</span></span> <span data-ttu-id="a7562-108">Ce fonctoid requiert quatre paramètres d'entrée dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="a7562-108">This functoid requires four input parameters in the following order:</span></span>  
  
    -   <span data-ttu-id="a7562-109">Une valeur de recherche</span><span class="sxs-lookup"><span data-stu-id="a7562-109">A lookup value</span></span>  
  
    -   <span data-ttu-id="a7562-110">Une chaîne de connexion à la base de données</span><span class="sxs-lookup"><span data-stu-id="a7562-110">A database connection string</span></span>  
  
    -   <span data-ttu-id="a7562-111">Un nom de table</span><span class="sxs-lookup"><span data-stu-id="a7562-111">A table name</span></span>  
  
    -   <span data-ttu-id="a7562-112">Un nom de colonne pour la valeur de recherche</span><span class="sxs-lookup"><span data-stu-id="a7562-112">A column name for the lookup value.</span></span>  
  
-   <span data-ttu-id="a7562-113">**Retour d’erreur.**</span><span class="sxs-lookup"><span data-stu-id="a7562-113">**Error Return.**</span></span> <span data-ttu-id="a7562-114">Utilisez le **retour d’erreur** fonctoid pour capturer les informations d’erreur, tels que les échecs de connexion de base de données, qui se produisent pendant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a7562-114">Use the **Error Return** functoid to capture error information, such as database connection failures, that occur during run time.</span></span> <span data-ttu-id="a7562-115">Ce fonctoid requiert un paramètre d’entrée : un lien à partir de la **recherche de base de données** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="a7562-115">This functoid requires one input parameter: a link from the **Database Lookup** functoid.</span></span>  
  
-   <span data-ttu-id="a7562-116">**Message de format.**</span><span class="sxs-lookup"><span data-stu-id="a7562-116">**Format Message.**</span></span> <span data-ttu-id="a7562-117">renvoie une chaîne formatée et localisée utilisant une substitution d'argument et, potentiellement, des références croisées d'ID et de valeurs.</span><span class="sxs-lookup"><span data-stu-id="a7562-117">Returns a formatted and localized string using argument substitution and, potentially, ID and value cross-referencing.</span></span>  
  
-   <span data-ttu-id="a7562-118">**Obtenir l’ID d’Application.**</span><span class="sxs-lookup"><span data-stu-id="a7562-118">**Get Application ID.**</span></span> <span data-ttu-id="a7562-119">extrait un identificateur pour un objet d'application.</span><span class="sxs-lookup"><span data-stu-id="a7562-119">Retrieves an identifier for an application object.</span></span>  
  
-   <span data-ttu-id="a7562-120">**Obtenir la valeur de l’Application.**</span><span class="sxs-lookup"><span data-stu-id="a7562-120">**Get Application Value.**</span></span> <span data-ttu-id="a7562-121">extrait une valeur d'application.</span><span class="sxs-lookup"><span data-stu-id="a7562-121">Retrieves an application value.</span></span>  
  
-   <span data-ttu-id="a7562-122">**Obtenir l’ID courant :**</span><span class="sxs-lookup"><span data-stu-id="a7562-122">**Get Common ID.**</span></span> <span data-ttu-id="a7562-123">extrait un identificateur pour un objet commun.</span><span class="sxs-lookup"><span data-stu-id="a7562-123">Retrieves an identifier for a common object.</span></span>  
  
-   <span data-ttu-id="a7562-124">**Obtenir la valeur courante.**</span><span class="sxs-lookup"><span data-stu-id="a7562-124">**Get Common Value.**</span></span> <span data-ttu-id="a7562-125">extrait une valeur commune.</span><span class="sxs-lookup"><span data-stu-id="a7562-125">Retrieves a common value.</span></span>  
  
-   <span data-ttu-id="a7562-126">**Supprimer l’ID d’Application.**</span><span class="sxs-lookup"><span data-stu-id="a7562-126">**Remove Application ID.**</span></span> <span data-ttu-id="a7562-127">Supprime une valeur d’application.</span><span class="sxs-lookup"><span data-stu-id="a7562-127">Removes an application value.</span></span>  
  
-   <span data-ttu-id="a7562-128">**Définir l’ID courant**</span><span class="sxs-lookup"><span data-stu-id="a7562-128">**Set Common ID.**</span></span> <span data-ttu-id="a7562-129">Permet de définir et renvoyer un identificateur pour un objet courant.</span><span class="sxs-lookup"><span data-stu-id="a7562-129">Sets and returns an identifier for a common object.</span></span>  
  
-   <span data-ttu-id="a7562-130">**Extracteur de valeur.**</span><span class="sxs-lookup"><span data-stu-id="a7562-130">**Value Extractor.**</span></span> <span data-ttu-id="a7562-131">Utilisez le **extracteur de valeur** fonctoid pour extraire des données à partir de la colonne spécifiée dans un jeu d’enregistrements renvoyé par le **recherche de base de données** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="a7562-131">Use the **Value Extractor** functoid to extract data from the specified column in a recordset returned by the **Database Lookup** functoid.</span></span> <span data-ttu-id="a7562-132">Ce fonctoid requiert deux paramètres d’entrée : un lien vers le **recherche de base de données** fonctoid et un nom de colonne.</span><span class="sxs-lookup"><span data-stu-id="a7562-132">This functoid requires two input parameters: a link to the **Database Lookup** functoid and a column name.</span></span>  
  
 <span data-ttu-id="a7562-133">Sept de la **base de données** fonctoids : **formater Message, obtenir l’ID Application**, **obtenir la valeur Application**, **obtenir l’ID courant**, **Obtenir la valeur courante**, **supprimer l’identificateur d’Application**, et **définir l’ID courant**— sont **CrossReferencing** fonctoids.</span><span class="sxs-lookup"><span data-stu-id="a7562-133">Seven of the **Database** functoids— **Format Message, Get Application ID**, **Get Application Value**, **Get Common ID**, **Get Common Value**, **Remove Application ID**, and **Set Common ID**—are **CrossReferencing** functoids.</span></span> <span data-ttu-id="a7562-134">Ces fonctoids convertissent les ID et valeurs d'un message d'entrée en ID et valeurs requises dans le message de sortie.</span><span class="sxs-lookup"><span data-stu-id="a7562-134">These functoids translate IDs and values from an input message into the IDs and values needed in the output message.</span></span> <span data-ttu-id="a7562-135">Pour plus d’informations, consultez **référence des fonctoids de base de données** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="a7562-135">For more information, see **Database Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 

## <a name="example"></a><span data-ttu-id="a7562-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="a7562-136">Example</span></span>  
 <span data-ttu-id="a7562-137">L’exemple suivant utilise certaines le **base de données** fonctoids.</span><span class="sxs-lookup"><span data-stu-id="a7562-137">The following example uses some of the **Database** functoids.</span></span> <span data-ttu-id="a7562-138">Imaginez un grand détaillant dont les magasins sont répartis sur une zone géographique étendue.</span><span class="sxs-lookup"><span data-stu-id="a7562-138">Consider a large retail manufacturer with stores spread over a large geographical area.</span></span> <span data-ttu-id="a7562-139">Pour suivre les magasins, le siège attribue à chaque magasin d’un code unique appelé un **StoreID**.</span><span class="sxs-lookup"><span data-stu-id="a7562-139">To keep track of the stores, headquarters assigns each store a unique code called a **StoreID**.</span></span> <span data-ttu-id="a7562-140">En outre, le siège associe les informations suivantes à chaque **StoreID**:</span><span class="sxs-lookup"><span data-stu-id="a7562-140">Additionally, headquarters associates the following information with each **StoreID**:</span></span>  
  
-   <span data-ttu-id="a7562-141">StoreName</span><span class="sxs-lookup"><span data-stu-id="a7562-141">StoreName</span></span>  
  
-   <span data-ttu-id="a7562-142">StoreAddress</span><span class="sxs-lookup"><span data-stu-id="a7562-142">StoreAddress</span></span>  
  
-   <span data-ttu-id="a7562-143">Ville</span><span class="sxs-lookup"><span data-stu-id="a7562-143">City</span></span>  
  
-   <span data-ttu-id="a7562-144">PostalCode</span><span class="sxs-lookup"><span data-stu-id="a7562-144">PostalCode</span></span>  
  
-   <span data-ttu-id="a7562-145">StorePhoneNumber</span><span class="sxs-lookup"><span data-stu-id="a7562-145">StorePhoneNumber</span></span>  
  
-   <span data-ttu-id="a7562-146">StoreManager</span><span class="sxs-lookup"><span data-stu-id="a7562-146">StoreManager</span></span>  
  
 <span data-ttu-id="a7562-147">Ces informations sont stockées dans une base de données et communiquées régulièrement aux partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="a7562-147">This information is stored in a database and is distributed to trading partners on a regular basis.</span></span> <span data-ttu-id="a7562-148">L'ensemble des achats du détaillant sont effectués par le siège et non par les magasins.</span><span class="sxs-lookup"><span data-stu-id="a7562-148">For the manufacturer, all purchasing is done by headquarters, not the stores.</span></span> <span data-ttu-id="a7562-149">Lorsque le siège envoie un bon de commande aux partenaires commerciaux, en général, plusieurs magasins reçoivent les marchandises commandées à l'aide de cet unique bon de commande.</span><span class="sxs-lookup"><span data-stu-id="a7562-149">When headquarters sends a purchase order to the trading partners, it is common for multiple stores to receive merchandise ordered through the single purchase order.</span></span> <span data-ttu-id="a7562-150">Au lieu d’envoyer des informations de nom et l’adresse pour chaque magasin devant recevoir la marchandise, siège envoie simplement la **StoreID**.</span><span class="sxs-lookup"><span data-stu-id="a7562-150">Instead of sending name and address information for each store that is to receive merchandise, headquarters simply sends the **StoreID**.</span></span> <span data-ttu-id="a7562-151">Pour insérer les informations de nom et l’adresse dans l’avis d’expédition avancée, le partenaire commercial utilise le **base de données** fonctoids insère automatiquement ces informations dans le message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="a7562-151">To insert the name and address information into the advanced ship notice, the trading partner uses the **Database** functoids to automatically insert this information into the output instance message.</span></span> <span data-ttu-id="a7562-152">La figure suivante montre comment un partenaire commercial peut mettre en œuvre le remplacement du StoreID dans un mappage.</span><span class="sxs-lookup"><span data-stu-id="a7562-152">The following figure shows how a trading partner can implement the replacement of the StoreID in a map.</span></span>  
  
 <span data-ttu-id="a7562-153">![Mapper les fonctoids de base de données différente affichant. ] (../core/media/origdbfunctoids.gif "origdbfunctoids")</span><span class="sxs-lookup"><span data-stu-id="a7562-153">![Map showing  different database functoids.](../core/media/origdbfunctoids.gif "origdbfunctoids")</span></span>  
  
 <span data-ttu-id="a7562-154">Dans cette figure, le schéma source représente un bon de commande entrant, le schéma de destination un avis d'expédition avancée.</span><span class="sxs-lookup"><span data-stu-id="a7562-154">In the figure, the source schema represents an incoming purchase order; the destination schema represents an advanced ship notice.</span></span> <span data-ttu-id="a7562-155">Le **recherche de base de données** fonctoid Recherche l’enregistrement approprié dans la table de base de données appropriée.</span><span class="sxs-lookup"><span data-stu-id="a7562-155">The **Database Lookup** functoid finds the appropriate record from the appropriate database table.</span></span> <span data-ttu-id="a7562-156">Le **extracteur de valeur** fonctoids extraient la colonne appropriée à partir de l’enregistrement de recherche.</span><span class="sxs-lookup"><span data-stu-id="a7562-156">The **Value Extractor** functoids extract the appropriate column from the lookup record.</span></span> <span data-ttu-id="a7562-157">Le **retour d’erreur** fonctoid génère une chaîne contenant des informations sur l’erreur s’il existe des erreurs (telles que les échecs de connexion) en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a7562-157">The **Error Return** functoid outputs a string containing error information if there are errors (such as connection failures) at run time.</span></span>  
  
 <span data-ttu-id="a7562-158">Dans l’exemple précédent, le premier paramètre d’entrée est issu de la **StoreID** champ d’entrant bons de commande et les autres trois paramètres d’entrée sont des constantes configurées dans le **configurer \< Fonctoid\> fonctoid** boîte de dialogue pour le **recherche de base de données** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="a7562-158">In the previous example, the first input parameter is taken from the **StoreID** field of the incoming purchase order, and the remaining three input parameters are constants configured in the **Configure \<Functoid\> Functoid** dialog box for the **Database Lookup** functoid.</span></span> <span data-ttu-id="a7562-159">Il est possible de créer des liens à partir du schéma source afin de fournir des valeurs pour les quatre paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="a7562-159">It is possible to create links from the source schema to supply values for all four input parameters.</span></span>  
  
> [!NOTE]
>  * <span data-ttu-id="a7562-160">Vous ne pouvez pas utiliser certains types de données Microsoft SQL Server, tels que **texte**, **ntext**, et **image**, en tant que valeurs de recherche pour le **recherche de base de données** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="a7562-160">You cannot use some Microsoft SQL Server data types, such as **text**, **ntext**, and **image**, as lookup values for the **Database Lookup** functoid.</span></span> <span data-ttu-id="a7562-161">Le fonctoid requiert des types de données pouvant être représentés par une chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="a7562-161">The functoid requires data types that can be represented as a text string.</span></span>  
>
>  * <span data-ttu-id="a7562-162">S’il existe plusieurs enregistrements correspondant aux paramètres d’entrée de la **recherche de base de données** fonctoid, le **extracteur de valeur** fonctoid extrait des données uniquement à partir du premier enregistrement.</span><span class="sxs-lookup"><span data-stu-id="a7562-162">If there is more than one record matching the input parameters of the **Database Lookup** functoid, the **Value Extractor** functoid extracts data only from the first record.</span></span>  
>
>  * <span data-ttu-id="a7562-163">Dans les chaînes de connexion, utilisez l'authentification NT pour protéger les mots de passe par chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a7562-163">Use NT authentication in connection strings to protect passwords with encryption.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="a7562-164">Fonctoids disponibles</span><span class="sxs-lookup"><span data-stu-id="a7562-164">Available functoids</span></span>  
 <span data-ttu-id="a7562-165">Le **base de données** fonctoids sont :</span><span class="sxs-lookup"><span data-stu-id="a7562-165">The **Database** functoids are:</span></span> 

* <span data-ttu-id="a7562-166">Recherche dans la base de données</span><span class="sxs-lookup"><span data-stu-id="a7562-166">Database Lookup</span></span>
* <span data-ttu-id="a7562-167">Retour d'erreur</span><span class="sxs-lookup"><span data-stu-id="a7562-167">Error Return</span></span>
* <span data-ttu-id="a7562-168">Formater message</span><span class="sxs-lookup"><span data-stu-id="a7562-168">Format Message</span></span>
* <span data-ttu-id="a7562-169">Obtenir l'ID d'application</span><span class="sxs-lookup"><span data-stu-id="a7562-169">Get Application ID</span></span>
* <span data-ttu-id="a7562-170">Obtenir la valeur d'application</span><span class="sxs-lookup"><span data-stu-id="a7562-170">Get Application Value</span></span>
* <span data-ttu-id="a7562-171">Obtenir l'ID courant</span><span class="sxs-lookup"><span data-stu-id="a7562-171">Get Common ID</span></span>
* <span data-ttu-id="a7562-172">Obtenir la valeur courante</span><span class="sxs-lookup"><span data-stu-id="a7562-172">Get Common Value</span></span>
* <span data-ttu-id="a7562-173">Supprimer l'identificateur d'application</span><span class="sxs-lookup"><span data-stu-id="a7562-173">Remove Application ID</span></span>
* <span data-ttu-id="a7562-174">Définir l'ID courant</span><span class="sxs-lookup"><span data-stu-id="a7562-174">Set Common ID</span></span>
* <span data-ttu-id="a7562-175">Extracteur de valeur</span><span class="sxs-lookup"><span data-stu-id="a7562-175">Value Extractor</span></span>

<span data-ttu-id="a7562-176">Pour plus d’informations sur ces functiods, consultez la **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="a7562-176">For more details on these functiods, see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="a7562-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7562-177">See Also</span></span>  
-  [<span data-ttu-id="a7562-178">Ajout de fonctoids de base à une carte</span><span class="sxs-lookup"><span data-stu-id="a7562-178">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
-  <span data-ttu-id="a7562-179">**Référence des fonctoids de base de données**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="a7562-179">**Database Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>