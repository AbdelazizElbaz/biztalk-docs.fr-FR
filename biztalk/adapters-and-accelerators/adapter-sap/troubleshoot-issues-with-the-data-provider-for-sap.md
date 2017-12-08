---
title: "Résoudre les problèmes avec le fournisseur de données pour SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, troubleshooting
- troubleshooting, Data Provider for SAP
ms.assetid: 6fe9baed-0404-4f15-b76e-88cc11c5ff46
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba61b75f95fad429c70da42479f22a32fa4e5a65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-issues-with-the-data-provider-for-sap"></a><span data-ttu-id="f221d-102">Résoudre les problèmes avec le fournisseur de données pour SAP</span><span class="sxs-lookup"><span data-stu-id="f221d-102">Troubleshoot Issues with the Data Provider for SAP</span></span>
<span data-ttu-id="f221d-103">Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs de fonctionnement que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f221d-103">This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].</span></span>  
  
##  <a name="BKMK_SAPUnknownParam"></a><span data-ttu-id="f221d-104">Erreur de paramètre à l’aide du fournisseur de données pour SAP</span><span class="sxs-lookup"><span data-stu-id="f221d-104">Unknown Parameter error using the Data Provider for SAP</span></span>  
 <span data-ttu-id="f221d-105">**Problème**</span><span class="sxs-lookup"><span data-stu-id="f221d-105">**Problem**</span></span>  
  
 <span data-ttu-id="f221d-106">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] attribue l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="f221d-106">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] gives the following error:</span></span>  
  
```  
Microsoft.Data.SAPClient.SAPException: Failed to retrieve data from SAP server --- > Microsoft.ServiceModel.Channels.Common.XmlReaderParsingException: Unknown Parameter OUT_ZDATATABLE.  
```  
  
 <span data-ttu-id="f221d-107">**Cause**</span><span class="sxs-lookup"><span data-stu-id="f221d-107">**Cause**</span></span>  
  
 <span data-ttu-id="f221d-108">Les RFC personnalisé, Z_EXTRACT_DATA_OO, installé dans votre système SAP n’est pas la plus récente.</span><span class="sxs-lookup"><span data-stu-id="f221d-108">The custom RFC, Z_EXTRACT_DATA_OO, installed in your SAP system is not the latest.</span></span> <span data-ttu-id="f221d-109">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] utilise un RFC personnalisé, Z_EXTRACT_DATA_OO, pour effectuer des opérations SELECT sur la table SAP.</span><span class="sxs-lookup"><span data-stu-id="f221d-109">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC, Z_EXTRACT_DATA_OO, to perform SELECT operations on the SAP table.</span></span>  
  
 <span data-ttu-id="f221d-110">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="f221d-110">**Resolution**</span></span>  
  
 <span data-ttu-id="f221d-111">Vous devez mettre à jour le RFC personnalisé à la dernière version disponible.</span><span class="sxs-lookup"><span data-stu-id="f221d-111">You must update the custom RFC to the latest available version.</span></span> <span data-ttu-id="f221d-112">Cette RFC, le Z_EXTRACT_DATA_OO, est disponible avec l’adapterpacknoversion.</span><span class="sxs-lookup"><span data-stu-id="f221d-112">This RFC, Z_EXTRACT_DATA_OO, is available with the adapterpacknoversion.</span></span> <span data-ttu-id="f221d-113">Pour plus d’informations sur la façon d’installer et désinstaller le RFC personnalisé, consultez [installer les RFC personnalisés pour le fournisseur de données pour SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span><span class="sxs-lookup"><span data-stu-id="f221d-113">For more information about how to install and uninstall the custom RFC, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).</span></span>
  
##  <a name="BKMK_SAPOOM"></a><span data-ttu-id="f221d-114">Exceptions de mémoire insuffisante lors de la sélection des données à partir d’une table SAP</span><span class="sxs-lookup"><span data-stu-id="f221d-114">Out of memory exceptions when selecting data from an SAP table</span></span>  
 <span data-ttu-id="f221d-115">**Problème**</span><span class="sxs-lookup"><span data-stu-id="f221d-115">**Problem**</span></span>  
  
 <span data-ttu-id="f221d-116">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] lève une exception de mémoire hors lors de la sélection des données à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="f221d-116">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] throws an out of memory exception when selecting data from an SAP system.</span></span>  
  
 <span data-ttu-id="f221d-117">**Cause**</span><span class="sxs-lookup"><span data-stu-id="f221d-117">**Cause**</span></span>  
  
 <span data-ttu-id="f221d-118">Par défaut, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] récupère les 10 000 lignes à la fois.</span><span class="sxs-lookup"><span data-stu-id="f221d-118">By default, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] retrieves 10,000 rows at a time.</span></span> <span data-ttu-id="f221d-119">En outre, chaque lot de lignes récupérées à partir du système SAP est stocké dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="f221d-119">Also, each batch of rows retrieved from the SAP system is stored in the memory.</span></span> <span data-ttu-id="f221d-120">Par conséquent,</span><span class="sxs-lookup"><span data-stu-id="f221d-120">So,</span></span>  
  
-   <span data-ttu-id="f221d-121">Si la table qui sont en cours extraites des données contient un grand nombre de lignes, ou</span><span class="sxs-lookup"><span data-stu-id="f221d-121">If the table from which data is being retrieved contains a large number of rows, or</span></span>  
  
-   <span data-ttu-id="f221d-122">Si la table contient des colonnes de types de données qui consomment une quantité importante de mémoire,</span><span class="sxs-lookup"><span data-stu-id="f221d-122">If the table contains columns of data types that consume a significant amount of memory,</span></span>  
  
 <span data-ttu-id="f221d-123">La consommation de mémoire par les [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] augmente considérablement et peut entraîner une absence d’exception de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f221d-123">The memory consumption by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] increases significantly and may result in an out of memory exception.</span></span>  
  
 <span data-ttu-id="f221d-124">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="f221d-124">**Resolution**</span></span>  
  
 <span data-ttu-id="f221d-125">Vous pouvez modifier le nombre maximal de lignes récupérées à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="f221d-125">You can change the maximum number of rows retrieved from the SAP system.</span></span> <span data-ttu-id="f221d-126">Vous pouvez le faire en spécifiant une option 'batchsize' avec l’instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="f221d-126">You can do so by specifying a 'batchsize' option with the SELECT statement.</span></span> <span data-ttu-id="f221d-127">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f221d-127">For example:</span></span>  
  
```  
SELECT * FROM <tablename> OPTION 'batchsize 1000'  
```  
  
 <span data-ttu-id="f221d-128">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] maintenant récupère uniquement les 1000 lignes à la fois et donc ne pas utiliser de grande quantité de mémoire.</span><span class="sxs-lookup"><span data-stu-id="f221d-128">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] now retrieves only 1000 rows at a time and hence does not consume large amount of memory.</span></span>  
  
##  <a name="BKMK_SAPQueryExcep"></a><span data-ttu-id="f221d-129">Exception lors de l’exécution d’une requête qui accepte des paramètres avec des valeurs de date</span><span class="sxs-lookup"><span data-stu-id="f221d-129">Exception while executing a query that takes parameters with date values</span></span>  
 <span data-ttu-id="f221d-130">**Problème**</span><span class="sxs-lookup"><span data-stu-id="f221d-130">**Problem**</span></span>  
  
 <span data-ttu-id="f221d-131">Vous obtenez l’exception suivante lorsque vous exécutez une requête à l’aide de la commande EXECQUERY qui a un paramètre qui accepte une valeur de date :</span><span class="sxs-lookup"><span data-stu-id="f221d-131">You get the following exception when you execute a query using the EXECQUERY command that has a parameter which takes a date value:</span></span>  
  
```  
ErrorCode=RFC_SYS_EXCEPTION. ErrorGroup=RFC_ERROR_SYSTEM_FAILURE.   
SapErrorMessage=Enter date in the format __.__.____.  
```  
  
 <span data-ttu-id="f221d-132">**Cause**</span><span class="sxs-lookup"><span data-stu-id="f221d-132">**Cause**</span></span>  
  
 <span data-ttu-id="f221d-133">Lors de l’exécution de requêtes à l’aide de la commande EXECQUERY, vous devez toujours spécifier les valeurs de date au format AAAAMMJJ.</span><span class="sxs-lookup"><span data-stu-id="f221d-133">When executing queries using the EXECQUERY command, you must always specify date values in YYYYMMDD format.</span></span>  
  
 <span data-ttu-id="f221d-134">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="f221d-134">**Resolution**</span></span>  
  
 <span data-ttu-id="f221d-135">Assurez-vous que vous spécifiez des valeurs de date au format AAAAMMJJ.</span><span class="sxs-lookup"><span data-stu-id="f221d-135">Make sure you specify date values in YYYYMMDD format.</span></span> <span data-ttu-id="f221d-136">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f221d-136">For example:</span></span>  
  
```  
EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1='20080606'  
```  
  
##  <a name="BKMK_SAPNOVARIANT"></a><span data-ttu-id="f221d-137">Exception NO_VARIANT l’exécution de requêtes à l’aide de la commande EXECQUERY</span><span class="sxs-lookup"><span data-stu-id="f221d-137">NO_VARIANT exception executing queries using the EXECQUERY command</span></span>  
 <span data-ttu-id="f221d-138">**Problème**</span><span class="sxs-lookup"><span data-stu-id="f221d-138">**Problem**</span></span>  
  
 <span data-ttu-id="f221d-139">Vous obtenez l’exception suivante lorsque vous exécutez une requête à l’aide de la commande EXECQUERY :</span><span class="sxs-lookup"><span data-stu-id="f221d-139">You get the following exception when you execute a query using the EXECQUERY command:</span></span>  
  
```  
Exception: Details: ErrorCode=RFC_EXCEPTION. ErrorGroup=RFC_ERROR_APPLICATION_EXCEPTION. SapErrorMessage=NO_VARIANT.  
AdapterErrorMessage=Error returned by RfcCallReceiveEx while calling RFC: <RFC name>  
```  
  
 <span data-ttu-id="f221d-140">**Cause**</span><span class="sxs-lookup"><span data-stu-id="f221d-140">**Cause**</span></span>  
  
 <span data-ttu-id="f221d-141">Il peut y avoir deux causes probables de cette exception :</span><span class="sxs-lookup"><span data-stu-id="f221d-141">There can be two probable causes for this exception:</span></span>  
  
1.  <span data-ttu-id="f221d-142">La requête que vous essayez d’exécuter a variantes définis dans le système SAP.</span><span class="sxs-lookup"><span data-stu-id="f221d-142">The query you are trying to execute has variants defined in the SAP system.</span></span> <span data-ttu-id="f221d-143">Variantes de faire référence à un jeu de critères de sélection que vous pouvez spécifier lors de l’exécution d’une requête SAP enregistré.</span><span class="sxs-lookup"><span data-stu-id="f221d-143">Variants refer to a saved set of selection criteria that you can specify while executing an SAP query.</span></span> <span data-ttu-id="f221d-144">Par exemple, vous pouvez utiliser les variantes pour spécifier les valeurs par défaut pour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="f221d-144">For example, you can use variants to specify default values for queries.</span></span>  
  
2.  <span data-ttu-id="f221d-145">La requête que vous essayez d’exécuter aucune des deux a une variante définie ni il attend une valeur de paramètre à passer.</span><span class="sxs-lookup"><span data-stu-id="f221d-145">The query you are trying to execute neither has a variant defined nor it expects a parameter value to be passed.</span></span>  
  
 <span data-ttu-id="f221d-146">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="f221d-146">**Resolution**</span></span>  
  
1.  <span data-ttu-id="f221d-147">Pour une raison 1, assurez-vous que vous spécifiez le nom de la variante associé à la requête.</span><span class="sxs-lookup"><span data-stu-id="f221d-147">For reason 1, make sure you specify the name of the variant associated with the query.</span></span> <span data-ttu-id="f221d-148">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f221d-148">For example:</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant =  ‘variant1’  
    ```  
  
2.  <span data-ttu-id="f221d-149">Pour une raison 2, assurez-vous que vous fournissez un nom de paramètre factice et la valeur lors de la spécification de la commande de requête.</span><span class="sxs-lookup"><span data-stu-id="f221d-149">For reason 2, make sure you provide a dummy parameter name and value while specifying the query command.</span></span> <span data-ttu-id="f221d-150">Par exemple, si « myquery » requête ne nécessite pas de n’importe quel paramètre à exécuter, la commande EXECQUERY doit être spécifiée en tant que :</span><span class="sxs-lookup"><span data-stu-id="f221d-150">For example, if “myquery” query does not require any parameter to execute, the EXECQUERY command must be specified as:</span></span>  
  
    ```  
    EXECQUERY myquery @usergroup='mygroup',@P1 = 'dummy_value'  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f221d-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f221d-151">See Also</span></span>  
[<span data-ttu-id="f221d-152">Résoudre les problèmes de l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="f221d-152">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)