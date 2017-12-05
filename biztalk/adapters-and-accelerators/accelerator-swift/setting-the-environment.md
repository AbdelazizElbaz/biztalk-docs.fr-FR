---
title: "Configuration de l’environnement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43027efc-acec-4110-96bd-cc4a19daaeab
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f0c63671833a394e0c750561d90c12c6476515f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="setting-the-environment"></a><span data-ttu-id="d7fe4-102">Configuration de l’environnement</span><span class="sxs-lookup"><span data-stu-id="d7fe4-102">Setting the Environment</span></span>
<span data-ttu-id="d7fe4-103">**Pour définir l’environnement :**</span><span class="sxs-lookup"><span data-stu-id="d7fe4-103">**To set the environment:**</span></span>  
  
1.  <span data-ttu-id="d7fe4-104">Assurez-vous que le Pack de messages SWIFT est configuré.</span><span class="sxs-lookup"><span data-stu-id="d7fe4-104">Make sure SWIFT Message Pack is configured.</span></span> <span data-ttu-id="d7fe4-105">Consultez la documentation du Pack de messages Swift pour configurer la même.</span><span class="sxs-lookup"><span data-stu-id="d7fe4-105">Refer to the Swift Message Pack documentation to configure the same.</span></span>  
  
2.  <span data-ttu-id="d7fe4-106">Exécutez le script SQL  *\<lecteur\>*: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tools\DataImport\CreateProceduresScript.sql.</span><span class="sxs-lookup"><span data-stu-id="d7fe4-106">Run the SQL script *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools\DataImport\CreateProceduresScript.sql.</span></span> <span data-ttu-id="d7fe4-107">Modifiez le nom de la base de données dans le script sql si le Swift et MessagePack sont configurés pour le nom de la base de données autre que A4Swift.</span><span class="sxs-lookup"><span data-stu-id="d7fe4-107">Change the database name in the sql script if the Swift and MessagePack are configured for database name other than A4Swift.</span></span>  
  
3.  <span data-ttu-id="d7fe4-108">Définir la valeur de clé « datasource » comme nom d’ordinateur et la clé « database » comme nom de la base de données (pour lesquels la Swift et MessagePack est configuré) dans le fichier  *\<lecteur\>*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools\DataImport\DataImport.exe.config.</span><span class="sxs-lookup"><span data-stu-id="d7fe4-108">Set the value of Key “datasource” as ComputerName and key “database” as database name (for which the Swift and MessagePack is configured) in the file *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools\DataImport\DataImport.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7fe4-109">Le fichier de données d’entrée ne doit pas être dans le même dossier que le fichier DataImport.exe.</span><span class="sxs-lookup"><span data-stu-id="d7fe4-109">The data input file should not be in the same folder as the DataImport.exe file.</span></span>  
  
4.  <span data-ttu-id="d7fe4-110">Exécutez l’utilitaire DataImport pour importer des données dans les tables BICplusIBAN et SEPA.</span><span class="sxs-lookup"><span data-stu-id="d7fe4-110">Run the DataImport utility to import data in BICplusIBAN and SEPA tables.</span></span>