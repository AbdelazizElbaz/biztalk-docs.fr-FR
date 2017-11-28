---
title: "Développement d’un fonctoid cumulé personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ea2c5fa-ed50-4b76-aee9-0d4adf9e6d8c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f69ae870269948358f117b07f37d481faced160
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-custom-cumulative-functoid"></a><span data-ttu-id="23f8f-102">Développement d'un fonctoid cumulé personnalisé</span><span class="sxs-lookup"><span data-stu-id="23f8f-102">Developing a Custom Cumulative Functoid</span></span>
<span data-ttu-id="23f8f-103">Utilisez un fonctoid cumulé personnalisé afin d'effectuer des opérations de cumul pour les valeurs qui apparaissent plusieurs fois dans un message d'instance.</span><span class="sxs-lookup"><span data-stu-id="23f8f-103">Use a custom cumulative functoid to perform accumulation operations for values that occur multiple times within an instance message.</span></span>  
  
 <span data-ttu-id="23f8f-104">Lorsque vous développez un fonctoid cumulé, vous devez implémenter trois fonctions.</span><span class="sxs-lookup"><span data-stu-id="23f8f-104">You must implement three functions when developing a cumulative functoid.</span></span> <span data-ttu-id="23f8f-105">Ces fonctions correspondent aux actions d'initialisation, de cumul et d'obtention dont le mappage a besoin pour effectuer le cumul.</span><span class="sxs-lookup"><span data-stu-id="23f8f-105">The three functions correspond to the initialize, cumulate, and get actions that the map needs to perform the accumulation.</span></span> <span data-ttu-id="23f8f-106">Avant d'aborder ces fonctions, il est important de traiter le thème de la sécurité des threads.</span><span class="sxs-lookup"><span data-stu-id="23f8f-106">Before discussing these functions it is important to discuss thread safety.</span></span>  
  
## <a name="writing-a-thread-safe-functoid"></a><span data-ttu-id="23f8f-107">Écriture d'un fonctoid thread-safe</span><span class="sxs-lookup"><span data-stu-id="23f8f-107">Writing a Thread-Safe Functoid</span></span>  
 <span data-ttu-id="23f8f-108">Le code du fonctoid doit être thread-safe car, dans les situations de stress, plusieurs instances d'un mappage sont susceptibles d'être exécutées simultanément.</span><span class="sxs-lookup"><span data-stu-id="23f8f-108">The functoid code must be thread-safe because under stress conditions multiple instances of a map may be running concurrently.</span></span> <span data-ttu-id="23f8f-109">Voici quelques-uns des points à ne pas oublier :</span><span class="sxs-lookup"><span data-stu-id="23f8f-109">Some of the points to remember include:</span></span>  
  
-   <span data-ttu-id="23f8f-110">L'état statique doit être thread-safe.</span><span class="sxs-lookup"><span data-stu-id="23f8f-110">Static state must be thread-safe.</span></span>  
  
-   <span data-ttu-id="23f8f-111">L'état d'instance ne doit pas toujours être thread-safe.</span><span class="sxs-lookup"><span data-stu-id="23f8f-111">Instance state does not always need to be thread-safe.</span></span>  
  
-   <span data-ttu-id="23f8f-112">Votre conception doit tenir compte d'une exécution dans des conditions de stress élevé.</span><span class="sxs-lookup"><span data-stu-id="23f8f-112">Design with consideration for running under high-stress conditions.</span></span> <span data-ttu-id="23f8f-113">Évitez les verrous dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="23f8f-113">Avoid taking locks whenever possible.</span></span>  
  
-   <span data-ttu-id="23f8f-114">Évitez la nécessité de synchronisation si possible.</span><span class="sxs-lookup"><span data-stu-id="23f8f-114">Avoid the need for synchronization if possible.</span></span>  
  
 <span data-ttu-id="23f8f-115">BizTalk Server fournit un mécanisme simple pour réduire la complexité de l'écriture d'un fonctoid cumulé thread-safe.</span><span class="sxs-lookup"><span data-stu-id="23f8f-115">BizTalk Server provides a simple mechanism to reduce the complexity of writing a thread-safe cumulative functoid.</span></span> <span data-ttu-id="23f8f-116">Les trois fonctions ont le même premier paramètre, à savoir une valeur d'index entière.</span><span class="sxs-lookup"><span data-stu-id="23f8f-116">All three functions have the same first parameter, an integer index value.</span></span> <span data-ttu-id="23f8f-117">BizTalk Server affecte un numéro unique à la valeur d'index lorsqu'il appelle votre fonction d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="23f8f-117">BizTalk Server assigns a unique number to the index value when it calls your initialization function.</span></span> <span data-ttu-id="23f8f-118">Vous pouvez utiliser cette valeur comme index dans un tableau contenant des valeurs s'accumulant, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="23f8f-118">You can use this value as an index into an array that holds accumulating values, as shown in the following code:</span></span>  
  
```  
private HashTable cumulativeArray = new HashTable();  
…  
// Initialization function  
public string InitCumulativeMultiply(int index)  
{  
    cumulativeArray[index] = 1.0;  
    return string.Empty;  
}  
```  
  
 <span data-ttu-id="23f8f-119">Cet exemple utilise un HashTable au lieu d'un ArrayList.</span><span class="sxs-lookup"><span data-stu-id="23f8f-119">This example uses a HashTable instead of an ArrayList.</span></span> <span data-ttu-id="23f8f-120">Cela est dû au fait que la fonction d'initialisation est susceptible de ne pas être appelée avec des valeurs d'index chronologiques.</span><span class="sxs-lookup"><span data-stu-id="23f8f-120">This is because the initialization function might not be called with in-order index values.</span></span>  
  
## <a name="implementing-the-three-cumulative-functions"></a><span data-ttu-id="23f8f-121">Implémentation des trois fonctions cumulées</span><span class="sxs-lookup"><span data-stu-id="23f8f-121">Implementing the Three Cumulative Functions</span></span>  
 <span data-ttu-id="23f8f-122">Vous devrez implémenter trois fonctions pour chaque fonctoid cumulé personnalisé que vous développez.</span><span class="sxs-lookup"><span data-stu-id="23f8f-122">You will need to implement three functions for each custom cumulative functoid you develop.</span></span> <span data-ttu-id="23f8f-123">Les fonctions et les méthodes que vous devez appeler dans le constructeur pour les définir sont résumées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="23f8f-123">The functions and the methods you must call in the constructor to set them are summarized in the following table.</span></span> <span data-ttu-id="23f8f-124">Toutes les fonctions retournent des valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="23f8f-124">All of the functions return string values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23f8f-125">Vous déterminez le meilleur nom pour chaque fonction, mais chaque fonction doit avoir le nombre et le type d'arguments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="23f8f-125">You determine the best name for each function, but each function must have the number and type of arguments specified.</span></span>  
  
|<span data-ttu-id="23f8f-126">Objectif de la fonction</span><span class="sxs-lookup"><span data-stu-id="23f8f-126">Function Purpose</span></span>|<span data-ttu-id="23f8f-127">Arguments</span><span class="sxs-lookup"><span data-stu-id="23f8f-127">Arguments</span></span>|<span data-ttu-id="23f8f-128">Pour définir une référence</span><span class="sxs-lookup"><span data-stu-id="23f8f-128">To set a reference</span></span>|<span data-ttu-id="23f8f-129">Pour définir le script en ligne</span><span class="sxs-lookup"><span data-stu-id="23f8f-129">To set inline script</span></span>|  
|----------------------|---------------|------------------------|--------------------------|  
|<span data-ttu-id="23f8f-130">Initialisation</span><span class="sxs-lookup"><span data-stu-id="23f8f-130">Initialization</span></span>|<span data-ttu-id="23f8f-131">**index de type int**</span><span class="sxs-lookup"><span data-stu-id="23f8f-131">**int index**</span></span>|<span data-ttu-id="23f8f-132">**SetExternalFunctionName**</span><span class="sxs-lookup"><span data-stu-id="23f8f-132">**SetExternalFunctionName**</span></span>|<span data-ttu-id="23f8f-133">**SetScriptBuffer** avec `functionNumber` = 0</span><span class="sxs-lookup"><span data-stu-id="23f8f-133">**SetScriptBuffer** with `functionNumber` = 0</span></span>|  
|<span data-ttu-id="23f8f-134">Cumul</span><span class="sxs-lookup"><span data-stu-id="23f8f-134">Cumulation</span></span>|<span data-ttu-id="23f8f-135">**int index, val, l’étendue de la chaîne de la chaîne**</span><span class="sxs-lookup"><span data-stu-id="23f8f-135">**int index, string val, string scope**</span></span>|<span data-ttu-id="23f8f-136">**SetExternalFunctionName2**</span><span class="sxs-lookup"><span data-stu-id="23f8f-136">**SetExternalFunctionName2**</span></span>|<span data-ttu-id="23f8f-137">**SetScriptBuffer** avec `functionNumber` = 1</span><span class="sxs-lookup"><span data-stu-id="23f8f-137">**SetScriptBuffer** with `functionNumber` = 1</span></span>|  
|<span data-ttu-id="23f8f-138">Obtenir</span><span class="sxs-lookup"><span data-stu-id="23f8f-138">Get</span></span>|<span data-ttu-id="23f8f-139">**index de type int**</span><span class="sxs-lookup"><span data-stu-id="23f8f-139">**int index**</span></span>|<span data-ttu-id="23f8f-140">**SetExternalFunctionName3**</span><span class="sxs-lookup"><span data-stu-id="23f8f-140">**SetExternalFunctionName3**</span></span>|<span data-ttu-id="23f8f-141">**SetScriptBuffer** avec `functionNumber` = 2</span><span class="sxs-lookup"><span data-stu-id="23f8f-141">**SetScriptBuffer** with `functionNumber` = 2</span></span>|  
  
### <a name="initialization"></a><span data-ttu-id="23f8f-142">Initialisation</span><span class="sxs-lookup"><span data-stu-id="23f8f-142">Initialization</span></span>  
 <span data-ttu-id="23f8f-143">L'initialisation vous permet de préparer les mécanismes que vous utiliserez pour procéder au cumul.</span><span class="sxs-lookup"><span data-stu-id="23f8f-143">Initialization enables you to prepare the mechanisms you will use to perform accumulation.</span></span> <span data-ttu-id="23f8f-144">Selon vos besoins, vous pouvez initialiser un tableau, réinitialiser une ou plusieurs valeurs ou charger d'autres ressources.</span><span class="sxs-lookup"><span data-stu-id="23f8f-144">You can initialize an array, reset one or more values, or load other resources as needed.</span></span> <span data-ttu-id="23f8f-145">La valeur de retour de chaîne n'est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="23f8f-145">The string return value is not used.</span></span>  
  
### <a name="cumulation"></a><span data-ttu-id="23f8f-146">Cumul</span><span class="sxs-lookup"><span data-stu-id="23f8f-146">Cumulation</span></span>  
 <span data-ttu-id="23f8f-147">C'est là que vous effectuez l'opération de cumul appropriée à votre fonctoid.</span><span class="sxs-lookup"><span data-stu-id="23f8f-147">This is where you perform the accumulation operation appropriate for your functoid.</span></span> <span data-ttu-id="23f8f-148">BizTalk Server transmet les trois paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="23f8f-148">BizTalk Server passes in the following three parameters:</span></span>  
  
-   <span data-ttu-id="23f8f-149">**Index.**</span><span class="sxs-lookup"><span data-stu-id="23f8f-149">**Index.**</span></span> <span data-ttu-id="23f8f-150">valeur entière représentant une instance de mappage.</span><span class="sxs-lookup"><span data-stu-id="23f8f-150">An integer value representing a map instance.</span></span> <span data-ttu-id="23f8f-151">Il peut y avoir plusieurs instances de mappage exécutées simultanément.</span><span class="sxs-lookup"><span data-stu-id="23f8f-151">There may be multiple map instances running concurrently.</span></span>  
  
-   <span data-ttu-id="23f8f-152">**Val.**</span><span class="sxs-lookup"><span data-stu-id="23f8f-152">**Val.**</span></span> <span data-ttu-id="23f8f-153">chaîne contenant la valeur qui doit être cumulée.</span><span class="sxs-lookup"><span data-stu-id="23f8f-153">A string containing the value that should be accumulated.</span></span> <span data-ttu-id="23f8f-154">À moins que vous n'écriviez un fonctoid cumulé de chaîne, il s'agit d'une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="23f8f-154">Unless you are writing a string Cumulate functoid it is a numeric value.</span></span>  
  
-   <span data-ttu-id="23f8f-155">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="23f8f-155">**Scope.**</span></span> <span data-ttu-id="23f8f-156">: chaîne contenant un nombre indiquant quelle valeur d'élément ou d'attribut doit être cumulée.</span><span class="sxs-lookup"><span data-stu-id="23f8f-156">A string containing a number indicating which element or attribute value should be accumulated.</span></span> <span data-ttu-id="23f8f-157">Les valeurs réelles sont déterminées par une implémentation.</span><span class="sxs-lookup"><span data-stu-id="23f8f-157">Actual values are determined by an implementation.</span></span>  
  
 <span data-ttu-id="23f8f-158">Vous décidez des valeurs à cumuler et des valeurs à ignorer.</span><span class="sxs-lookup"><span data-stu-id="23f8f-158">You decide which values to accumulate and which values to ignore.</span></span> <span data-ttu-id="23f8f-159">Vous pouvez par exemple ignorer les valeurs qui ne sont pas inférieures à 0 et lever une exception lorsqu'une valeur n'est pas numérique.</span><span class="sxs-lookup"><span data-stu-id="23f8f-159">For example, you may ignore values that are not below 0 but throw an exception when a value is not numeric.</span></span> <span data-ttu-id="23f8f-160">**BaseFunctoid** fournit deux fonctions :**IsDate** et **IsNumeric**, pour faciliter la validation.</span><span class="sxs-lookup"><span data-stu-id="23f8f-160">**BaseFunctoid** supplies two functions—**IsDate** and **IsNumeric**—to assist with validation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23f8f-161">Si vous utilisez **IsDate** ou **IsNumeric** dans un script inline, veillez à définir **RequiredGlobalHelperFunctions** afin que les fonctions sont rendues disponibles pour votre script.</span><span class="sxs-lookup"><span data-stu-id="23f8f-161">If you use **IsDate** or **IsNumeric** in an inline script, be sure to set **RequiredGlobalHelperFunctions** so that the functions are made available to your script.</span></span>  
  
 <span data-ttu-id="23f8f-162">La valeur de retour de chaîne n'est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="23f8f-162">The string return value is not used.</span></span>  
  
### <a name="get"></a><span data-ttu-id="23f8f-163">Obtenir</span><span class="sxs-lookup"><span data-stu-id="23f8f-163">Get</span></span>  
 <span data-ttu-id="23f8f-164">Lorsque BizTalk Server termine son itération parmi toutes les valeurs déterminées par les paramètres de fonctoid dans le mappage, il demande la valeur cumulée.</span><span class="sxs-lookup"><span data-stu-id="23f8f-164">When BizTalk Server finishes iterating through all of the values determined by the functoid settings in the map, it requests the accumulated value.</span></span> <span data-ttu-id="23f8f-165">La fonction d'obtention comprend un argument, `Index`, qui est une valeur entière représentant une instance de mappage.</span><span class="sxs-lookup"><span data-stu-id="23f8f-165">The get function has one argument, `Index`, which is an integer value representing a map instance.</span></span> <span data-ttu-id="23f8f-166">Votre fonction doit utiliser la valeur d'index pour rechercher et renvoyer la valeur cumulée sous la forme d'une chaîne.</span><span class="sxs-lookup"><span data-stu-id="23f8f-166">Your function should use the index value to find and return the accumulated value as a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23f8f-167">Exemple</span><span class="sxs-lookup"><span data-stu-id="23f8f-167">Example</span></span>  
 <span data-ttu-id="23f8f-168">L'exemple ci-dessous illustre comment créer un fonctoid personnalisé pour effectuer la multiplication cumulée.</span><span class="sxs-lookup"><span data-stu-id="23f8f-168">The following example illustrates how to create a custom functoid for performing cumulative multiplication.</span></span> <span data-ttu-id="23f8f-169">Il repose sur un fichier de ressources contenant trois ressources de chaîne et une ressource bitmap 16 x 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="23f8f-169">It relies on a resource file containing three string resources and a 16x16-pixel bitmap resource.</span></span>  
  
```  
using System;  
using Microsoft.BizTalk.BaseFunctoids;  
using System.Reflection;  
using System.Text;  
using System.Collections;  
using System.Globalization;  
  
namespace Microsoft.Samples.BizTalk.CustomFunctoid  
{  
    public class CumulativeMultiplyFunctoid : BaseFunctoid  
    {  
        private ArrayList myCumulativeArray = new ArrayList();  
  
        public CumulativeMultiplyFunctoid() : base()  
        {  
            //ID for this functoid  
            ID = 6001;  
  
            // Resource assembly must be ProjectName.ResourceName if building with VS.Net  
            SetupResourceAssembly("Microsoft.Samples.BizTalk.CustomFunctoid.CustomFunctoidResources", Assembly.GetExecutingAssembly());  
  
            // Pass the resource ID names for functoid name, tooltip  
            // description and the 16x16 bitmap for the Map palette  
            SetName("IDS_CUMULATIVEMULTIPLYFUNCTOID_NAME");  
            SetTooltip("IDS_CUMULATIVEMULTIPLYFUNCTOID_TOOLTIP");  
            SetDescription("IDS_CUMULATIVEMULTIPLYFUNCTOID_DESCRIPTION");  
            SetBitmap("IDB_CUMULATIVEMULTIPLYFUNCTOID_BITMAP");  
  
            // Put this string handling function under the Cumulative  
            // Functoid tab in the Visual Studio toolbox for functoids  
            Category = FunctoidCategory.Cumulative;  
  
            // 2 required parameters, no optional parameters  
            SetMinParams(1);  
            SetMaxParams(2);  
  
            // Functoid accepts three inputs  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
            AddInputConnectionType((~ConnectionType.FunctoidCount) & (~ConnectionType.FunctoidIndex) & (~ConnectionType.FunctoidIteration) & (~ConnectionType.FunctoidCumulative) & (~ConnectionType.FunctoidLooping) & (~ConnectionType.Record));  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
  
            // Set the output connection type  
            OutputConnectionType = ConnectionType.AllExceptRecord;  
  
            // Set the Initialize, Cumulative and Get functions  
            SetExternalFunctionName(GetType().Assembly.FullName, "Microsoft.Samples.BizTalk.CustomFunctoid.CumulativeMultiplyFunctoid", "InitCumulativeMultiply");  
            SetExternalFunctionName2("AddToCumulativeMultiply");  
            SetExternalFunctionName3("GetCumulativeMultiply");  
        }  
  
        // Initialization function  
        public string InitCumulativeMultiply(int index)  
        {  
            if (index >= 0)  
            {  
                if (index >= myCumulativeArray.Count)  
                {  
                    myCumulativeArray.Add(1.0);  
                }  
                else  
                {  
                    myCumulativeArray[index] = 1.0;  
                }  
            }  
  
            return "";  
        }  
  
        // Cumulative function  
        public string AddToCumulativeMultiply(int index, string val, string reserved)  
        {  
            if (index < 0 || index >= myCumulativeArray.Count)  
            {  
                return "";  
            }  
  
            if (IsNumeric(val))  
            {  
                double dval = Convert.ToDouble(val, CultureInfo.InvariantCulture);  
                myCumulativeArray[index] = (double)(myCumulativeArray[index]) * dval;  
            }  
            return myCumulativeArray[index].ToString();  
        }  
  
        // Get Function  
        public string GetCumulativeMultiply(int index)  
        {  
            if (index < 0 || index >= myCumulativeArray.Count)  
            {  
                return "";  
            }  
  
            return myCumulativeArray[index].ToString();  
        }  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="23f8f-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23f8f-170">See Also</span></span>  
 <span data-ttu-id="23f8f-171">[Utilisation de BaseFunctoid](../core/using-basefunctoid.md) </span><span class="sxs-lookup"><span data-stu-id="23f8f-171">[Using BaseFunctoid](../core/using-basefunctoid.md) </span></span>  
 <span data-ttu-id="23f8f-172">[Développement d’un fonctoid Inline personnalisé](../core/developing-a-custom-inline-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="23f8f-172">[Developing a Custom Inline Functoid](../core/developing-a-custom-inline-functoid.md) </span></span>  
 [<span data-ttu-id="23f8f-173">Fonctoid personnalisé (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="23f8f-173">Custom Functoid (BizTalk Server Sample)</span></span>](../core/custom-functoid-biztalk-server-sample.md)