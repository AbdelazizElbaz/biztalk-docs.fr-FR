---
title: "Appeler les RFC et BAPI dans SAP à l’aide de la commande EXEC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EXEC command, invoking RFCs and BAPIs
- BAPIs and RFCs, invoking by using the EXEC command
- RFCs and BAPIs, invoking by using the EXEC command
ms.assetid: 55443679-2fa8-4c13-ac3b-1c85b5166cd2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 500e0f932a8245f76954aa7a8785dbec012321e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-rfcs-and-bapis-using-the-exec-command-in-sap"></a><span data-ttu-id="327e4-102">Appeler les RFC et BAPI à l’aide de la commande EXEC dans SAP</span><span class="sxs-lookup"><span data-stu-id="327e4-102">Invoke RFCs and BAPIs using the EXEC Command in SAP</span></span>
<span data-ttu-id="327e4-103">Le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] expose le système SAP comme source de données ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="327e4-103">The [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] exposes the SAP system as an ADO.NET data source.</span></span> <span data-ttu-id="327e4-104">À l’aide de [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], vous pouvez appeler des RFC et BAPI sur le système SAP via une commande EXEC.</span><span class="sxs-lookup"><span data-stu-id="327e4-104">By using [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], you can invoke RFCs and BAPIs on the SAP system through an EXEC command.</span></span>  
  
## <a name="how-to-invoke-rfcs-and-bapis-on-the-sap-system"></a><span data-ttu-id="327e4-105">Comment appeler des RFC et BAPI sur le système SAP</span><span class="sxs-lookup"><span data-stu-id="327e4-105">How to Invoke RFCs and BAPIs on the SAP system</span></span>  
 <span data-ttu-id="327e4-106">Pour appeler un RFC ou BAPI à l’aide de la [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="327e4-106">To invoke an RFC or BAPI using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], perform the following steps:</span></span>  
  
#### <a name="to-invoke-an-rfc-or-bapi"></a><span data-ttu-id="327e4-107">Pour appeler RFC ou BAPI</span><span class="sxs-lookup"><span data-stu-id="327e4-107">To invoke an RFC or BAPI</span></span>  
  
1.  <span data-ttu-id="327e4-108">Inclure une référence (et un à l’aide d’instruction dans votre code) à **Microsoft.Data.SAPClient**.</span><span class="sxs-lookup"><span data-stu-id="327e4-108">Include a reference (and a using statement in your code) to **Microsoft.Data.SAPClient**.</span></span>  
  
2.  <span data-ttu-id="327e4-109">Créer un **SAPConnection** objet à l’aide d’un fournisseur de données pour la chaîne de connexion SAP.</span><span class="sxs-lookup"><span data-stu-id="327e4-109">Create a **SAPConnection** object by using a Data Provider for SAP connection string.</span></span> <span data-ttu-id="327e4-110">Pour plus d’informations sur la chaîne de connexion, consultez [en savoir plus sur les types de fournisseur de données pour la chaîne de connexion SAP](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span><span class="sxs-lookup"><span data-stu-id="327e4-110">For more information about the connection string, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
3.  <span data-ttu-id="327e4-111">Ouvrir une connexion au système SAP en appelant **ouvrir** sur la **SAPConnection**.</span><span class="sxs-lookup"><span data-stu-id="327e4-111">Open a connection to the SAP system by invoking **Open** on the **SAPConnection**.</span></span>  
  
4.  <span data-ttu-id="327e4-112">Créer un **SAPCommand** de l’objet à partir de la **SAPConnection**.</span><span class="sxs-lookup"><span data-stu-id="327e4-112">Create a **SAPCommand** object from the **SAPConnection**.</span></span>  
  
5.  <span data-ttu-id="327e4-113">Spécifiez l’appel BAPI ou RFC dans le **CommandText** propriété de la **SAPCommand**.</span><span class="sxs-lookup"><span data-stu-id="327e4-113">Specify the BAPI or RFC call in the **CommandText** property of the **SAPCommand**.</span></span> <span data-ttu-id="327e4-114">Si nécessaire, vous pouvez spécifier des paramètres à l’aide de **objet SAPParameter** objets.</span><span class="sxs-lookup"><span data-stu-id="327e4-114">If necessary, you can specify parameters using **SAPParameter** objects.</span></span> <span data-ttu-id="327e4-115">Pour plus d’informations sur la façon de spécifier un appel BAPI ou RFC à l’aide d’une instruction EXEC, consultez [syntaxe pour une instruction EXEC dans SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-exec-statement-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="327e4-115">For more information about how to specify a BAPI or RFC call using an EXEC statement, see [Syntax for an EXEC Statement in SAP](../../adapters-and-accelerators/adapter-sap/syntax-for-an-exec-statement-in-sap.md).</span></span> <span data-ttu-id="327e4-116">Pour obtenir des exemples montrant comment spécifier un BAPI ou les RFC, consultez [exemples pour l’instruction EXEC](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md).</span><span class="sxs-lookup"><span data-stu-id="327e4-116">For examples of how to specify a BAPI or RFC, see [Examples for EXEC Statement](../../adapters-and-accelerators/adapter-sap/examples-for-exec-statement.md).</span></span>  
  
6.  <span data-ttu-id="327e4-117">Exécutez la commande à appeler la RFC ou BAPI et obtenir les résultats dans un **SAPDataReader**.</span><span class="sxs-lookup"><span data-stu-id="327e4-117">Execute the command to invoke the RFC or BAPI and obtain the results in a **SAPDataReader**.</span></span>  
  
7.  <span data-ttu-id="327e4-118">Lisez les résultats à partir de la **SAPDataReader**.</span><span class="sxs-lookup"><span data-stu-id="327e4-118">Read the results from the **SAPDataReader**.</span></span>  
  
8.  <span data-ttu-id="327e4-119">Lorsque vous avez terminé, fermez (ou supprimer) le **SAPConnection** et **SAPDataReader**.</span><span class="sxs-lookup"><span data-stu-id="327e4-119">When you are finished using them, close (or dispose) the **SAPConnection** and the **SAPDataReader**.</span></span>  
  
 <span data-ttu-id="327e4-120">Le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] expose également un **SAPClientFactory** (classe), qui vous permet de créer **SAPConnection**, **SAPCommand** et **SAPConnection** objets.</span><span class="sxs-lookup"><span data-stu-id="327e4-120">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] also exposes a **SAPClientFactory** class, which you can use to create **SAPConnection**, **SAPCommand** and **SAPConnection** objects.</span></span> <span data-ttu-id="327e4-121">Pour plus d’informations sur les classes ADO.NET étendu par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], consultez [étendent les Interfaces ADO.NET avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="327e4-121">For more information about the ADO.NET classes extended by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Extend ADO.NET Interfaces with the SAP adapter](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="327e4-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="327e4-122">Example</span></span>  
 <span data-ttu-id="327e4-123">L’exemple suivant appelle SD_RFC_CUSTOMER_GET pour extraire les informations client pour tous les clients dont le nom commence par « AB ».</span><span class="sxs-lookup"><span data-stu-id="327e4-123">The following example invokes SD_RFC_CUSTOMER_GET to retrieve customer information for all customers whose names start with "AB".</span></span> <span data-ttu-id="327e4-124">Il écrit ensuite le client enregistre dans la console.</span><span class="sxs-lookup"><span data-stu-id="327e4-124">It then writes the customer records to the console.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using Microsoft.Data.SAPClient;  
  
namespace SapAdoExec  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string connstr = "TYPE=A; ASHOST=YourSAPHost; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;";  
  
            using (SAPConnection conn = new SAPConnection(connstr))  
            {  
                conn.Open();  
  
                using (SAPCommand cmd = conn.CreateCommand())  
                {  
                    cmd.CommandText = "exec sd_rfc_customer_get @name1='AB*' ";  
                    using (SAPDataReader dr = cmd.ExecuteReader())  
                    {  
                        do  
                        {  
                            int rows = 0;  
                            while (dr.Read())  
                            {  
                                rows++;  
                                StringBuilder b = new StringBuilder();  
                                for (int i = 0; i < dr.FieldCount; i++)  
                                {  
                                    b.Append(dr[i].ToString() + " ");  
                                }  
                                Console.WriteLine("row {0}: {1} ", rows, b.ToString());  
                            }  
                            Console.WriteLine("Number of rows:{0}", rows);  
                        } while (dr.NextResult());  
  
                    }  
                }  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="327e4-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="327e4-125">See Also</span></span>  
 <span data-ttu-id="327e4-126">[Utiliser le fournisseur de données .NET Framework pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md) </span><span class="sxs-lookup"><span data-stu-id="327e4-126">[Use the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md) </span></span>  
 [<span data-ttu-id="327e4-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="327e4-127">Samples</span></span>](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)