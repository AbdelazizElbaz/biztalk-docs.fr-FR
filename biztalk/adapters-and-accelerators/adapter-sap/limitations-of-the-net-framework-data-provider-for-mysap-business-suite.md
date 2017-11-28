---
title: "Limitations du fournisseur de données .NET Framework pour mySAP Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, limitations of
- .NET Framework Data Provider for mySAP Business Suite, limitations of
ms.assetid: 462e627d-41da-4456-bc62-e8cf7296f5b4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fd4ad3a57e2b762a53582ceb77eb65f23a535fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-the-net-framework-data-provider-for-mysap-business-suite"></a><span data-ttu-id="5c891-102">Limitations du fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="5c891-102">Limitations of the .NET Framework Data Provider for mySAP Business Suite</span></span>
<span data-ttu-id="5c891-103">Les éléments suivants sont connus des limitations de la [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) :</span><span class="sxs-lookup"><span data-stu-id="5c891-103">The following are known limitations of the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]):</span></span>  
  
-   <span data-ttu-id="5c891-104">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend pas en charge la connexion à un système SAP à l’aide de la connexion de réseau sécurisée (SNC).</span><span class="sxs-lookup"><span data-stu-id="5c891-104">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support connecting to an SAP system using Secure Network Connection (SNC).</span></span> <span data-ttu-id="5c891-105">Pour plus d’informations sur SNC, consultez [sécurité entre le système SAP et la carte](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="5c891-105">For more information about SNC, see [Security between the SAP system and the adapter](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md).</span></span>
  
-   <span data-ttu-id="5c891-106">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend pas en charge la `DbType` ou `Size` propriétés de la `SAPParameter`.</span><span class="sxs-lookup"><span data-stu-id="5c891-106">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support the `DbType` or `Size` properties of the `SAPParameter`.</span></span> <span data-ttu-id="5c891-107">Au lieu de cela, lorsque l’utilisateur spécifie une valeur pour le `SAPParameter`, la valeur est effectuée en interne pour un type de données .NET selon le mappage établi entre les types de données .NET et SAP.</span><span class="sxs-lookup"><span data-stu-id="5c891-107">Instead, when the user specifies a value for the `SAPParameter`, the value is cast internally to a .NET data type according to the established mapping between .NET and SAP data types.</span></span>  
  
-   <span data-ttu-id="5c891-108">La longueur maximale autorisée pour les valeurs de champ de types de données SAP `CURR`, `DEC`, et `QUAN` est 29 chiffres.</span><span class="sxs-lookup"><span data-stu-id="5c891-108">The maximum length allowed for field values of SAP data types `CURR`, `DEC`, and `QUAN` is 29 digits.</span></span> <span data-ttu-id="5c891-109">Bien que SAP fournit les 31 emplacements pour ces valeurs de type de données en mode natif, le type de données decimal .NET dans lequel ils sont convertis impose une limite de 29 chiffres.</span><span class="sxs-lookup"><span data-stu-id="5c891-109">Although SAP provides 31 places for these data-type values natively, the .NET decimal data type to which they are converted imposes a 29-digit limit.</span></span>  
  
-   <span data-ttu-id="5c891-110">Une limitation de mappage entre le type de données .NET `Double` et SAP `FLTP` type de données peut provoquer une erreur de dépassement de capacité lors de la lecture des données à partir du système SAP dans le type .NET.</span><span class="sxs-lookup"><span data-stu-id="5c891-110">A mapping limitation between the .NET data type `Double` and the SAP `FLTP` data type can cause an overflow error when reading data from the SAP system into the .NET type.</span></span> <span data-ttu-id="5c891-111">Bien que le type .NET peut représenter un nombre de 64 bits double précision avec des valeurs allant de moins 1, 79769313486232E308 à plus 1, 79769313486232E308, un SAP `FLTP` type analysé par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne peut pas dépasser 1.8446744073709552E + 19 ; la limite effective pour le `FLTP` type correspond à la plage négative 1.8446744073709552E + 19 1.8446744073709552E + 19 positif.</span><span class="sxs-lookup"><span data-stu-id="5c891-111">Although the .NET type can represent a double-precision 64-bit number with values ranging from negative 1.79769313486232e308 to positive 1.79769313486232e308, an SAP `FLTP` type parsed by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] cannot exceed 1.8446744073709552E+19; the effective limit for the `FLTP` type is the range negative 1.8446744073709552E+19 to positive 1.8446744073709552E+19.</span></span>  
  
-   <span data-ttu-id="5c891-112">En raison de problèmes de délai d’attente un traitement par la bibliothèque cliente sous-jacente, le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend pas en charge le délai d’attente de connexion et de commande.</span><span class="sxs-lookup"><span data-stu-id="5c891-112">Due to issues with timeout handling by the underlying client library, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support command and connection timeout.</span></span>  
  
-   <span data-ttu-id="5c891-113">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne prend pas en charge le comportement asynchrone de la commande.</span><span class="sxs-lookup"><span data-stu-id="5c891-113">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support asynchronous command behavior.</span></span>  
  
-   <span data-ttu-id="5c891-114">Lorsqu’il est utilisé avec un projet SQL Server Integration Services (SSIS), le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] ne parvient pas à récupérer des données pour les colonnes qui contiennent des valeurs avec plus de 8 000 caractères.</span><span class="sxs-lookup"><span data-stu-id="5c891-114">When used with a SQL Server Integration Services (SSIS) project, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] fails to retrieve data for columns that contain values with more than 8000 characters.</span></span> <span data-ttu-id="5c891-115">Il s’agit en raison d’une restriction SSIS en fonction desquelles :</span><span class="sxs-lookup"><span data-stu-id="5c891-115">This is due to an SSIS restriction according to which:</span></span>  
  
    -   <span data-ttu-id="5c891-116">Les valeurs supérieures à 4 000 caractères dans la variable SSIS ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5c891-116">Values greater than 4000 characters in SSIS variable are not supported.</span></span>  
  
    -   <span data-ttu-id="5c891-117">Les valeurs supérieures à 4 000 caractères larges ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5c891-117">Values greater than 4000 wide characters are not supported.</span></span>  
  
    -   <span data-ttu-id="5c891-118">Les valeurs supérieures à 8 000 caractères codés sur un octet ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5c891-118">Values greater than 8000 single-byte characters are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c891-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c891-119">See Also</span></span>  
 [<span data-ttu-id="5c891-120">Sur le fournisseur de données .NET Framework pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="5c891-120">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)