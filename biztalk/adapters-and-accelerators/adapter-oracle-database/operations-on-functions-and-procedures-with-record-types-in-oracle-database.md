---
title: Opérations sur les fonctions et procédures avec des Types d’enregistrements de base de données Oracle | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RECORD type
ms.assetid: 28ecb76c-de82-43df-83cc-917c482417b3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46daadeaa5d1fc1060217f044a9d143488c38d7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-procedures-with-record-types-in-oracle-database"></a><span data-ttu-id="27355-102">Opérations sur les fonctions et procédures avec des Types d’enregistrements de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="27355-102">Operations on Functions and Procedures with RECORD Types in Oracle Database</span></span>
<span data-ttu-id="27355-103">Types d’enregistrements Oracle sont utilisés pour représenter des informations hiérarchiques dans les paramètres passés aux procédures et fonctions de PL/SQL.</span><span class="sxs-lookup"><span data-stu-id="27355-103">Oracle RECORD types are used to represent hierarchical information in parameters passed to PL/SQL functions and procedures.</span></span> <span data-ttu-id="27355-104">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des types d’enregistrement en tant que types XML complexes.</span><span class="sxs-lookup"><span data-stu-id="27355-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces RECORD types as complex XML types.</span></span> <span data-ttu-id="27355-105">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge les types de types d’enregistrements suivants :</span><span class="sxs-lookup"><span data-stu-id="27355-105">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the following kinds of RECORD types:</span></span>  
  
-   <span data-ttu-id="27355-106">Types d’enregistrements qui sont déclarés en tant que TABLE % ROWTYPE paramètres dans les procédures stockées et fonctions.</span><span class="sxs-lookup"><span data-stu-id="27355-106">RECORD types that are declared as TABLE%ROWTYPE parameters in stored procedures and functions.</span></span>  
  
-   <span data-ttu-id="27355-107">Types d’enregistrements qui sont déclarés en tant que paramètres de TYPE d’enregistrement dans les packages de PL/SQL, par exemple, tapez rec_type1 est RECORD(name varchar2(100), age number(3));</span><span class="sxs-lookup"><span data-stu-id="27355-107">RECORD types that are declared as TYPE of RECORD parameters in PL/SQL packages for example, TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));</span></span>  
  
-   <span data-ttu-id="27355-108">Types d’enregistrements qui contiennent des enregistrements imbriqués.</span><span class="sxs-lookup"><span data-stu-id="27355-108">RECORD types that contain nested records.</span></span>  
  
-   <span data-ttu-id="27355-109">Types d’enregistrements qui s’affichent, OUT ou paramètres dans des procédures ou des fonctions.</span><span class="sxs-lookup"><span data-stu-id="27355-109">RECORD types that appear as IN, OUT, or IN OUT parameters to procedures or functions.</span></span>  
  
-   <span data-ttu-id="27355-110">Types d’enregistrements qui sont des valeurs de retour des fonctions.</span><span class="sxs-lookup"><span data-stu-id="27355-110">RECORD types that are RETURN values of functions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27355-111">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les types BFILE en tant que membres de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="27355-111">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support BFILE types as RECORD members.</span></span>  
  
 <span data-ttu-id="27355-112">Pour plus d’informations sur :</span><span class="sxs-lookup"><span data-stu-id="27355-112">For information about:</span></span>  
  
-   <span data-ttu-id="27355-113">Appeler une fonction ou procédure impliquant des types d’enregistrements à l’aide du modèle de service WCF, consultez [exécuter les opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="27355-113">Invoking a function or procedure involving RECORD types using the WCF service model, see [Run Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="27355-114">Appel d’une fonction ou procédure impliquant l’enregistrement à l’aide des types [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [appeler des fonctions et procédures avec des Types d’enregistrements à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="27355-114">Invoking a function or procedure involving RECORD types using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Invoke Functions and Procedures with RECORD Types by Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="27355-115">Structure XML de l’enregistrement des types pris en charge par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [des schémas de Message pour les Types d’enregistrements](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md).</span><span class="sxs-lookup"><span data-stu-id="27355-115">XML structure for RECORD types as supported by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Message Schemas for RECORD Types](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27355-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27355-116">See Also</span></span>  
 <span data-ttu-id="27355-117">[Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="27355-117">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>