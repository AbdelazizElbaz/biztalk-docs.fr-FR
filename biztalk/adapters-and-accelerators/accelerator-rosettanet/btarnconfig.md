---
title: BtarnConfig | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTARN, exporting configuration data
- BTARN, BtarnConfig utility
- BtarnConfig utility
- BTARN, importing configuration data
ms.assetid: 8c95be2a-7df5-47fb-ae2d-64fa27e2811a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9221e530266091795260bc7d4fd7e8788e066335
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btarnconfig"></a><span data-ttu-id="591f1-102">BtarnConfig</span><span class="sxs-lookup"><span data-stu-id="591f1-102">BtarnConfig</span></span>
<span data-ttu-id="591f1-103">Vous utilisez l’utilitaire BtarnConfig pour importer des données de configuration dans, ou exporter des données de configuration à partir, un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="591f1-103">You use the BtarnConfig utility to import configuration data into, or export configuration data from, a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] environment.</span></span> <span data-ttu-id="591f1-104">Ces données de configuration sont les données que vous définissez à l’aide de la Console de gestion BTARN, y compris les paramètres de configuration de processus, des organisations de base, des partenaires et des accords.</span><span class="sxs-lookup"><span data-stu-id="591f1-104">This configuration data is the data that you set by using the BTARN Management Console, including process configuration settings, home organizations, partners, and agreements.</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="591f1-105">Emplacement dans le kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="591f1-105">Location in SDK</span></span>  
 <span data-ttu-id="591f1-106">\<*lecteur*> \ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK</span><span class="sxs-lookup"><span data-stu-id="591f1-106">\<*drive*>\ Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK</span></span>  
  
## <a name="running-btarnconfig"></a><span data-ttu-id="591f1-107">BtarnConfig en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="591f1-107">Running BtarnConfig</span></span>  
  
#### <a name="to-run-btarnconfig"></a><span data-ttu-id="591f1-108">Pour exécuter BtarnConfig</span><span class="sxs-lookup"><span data-stu-id="591f1-108">To run BtarnConfig</span></span>  
  
1.  <span data-ttu-id="591f1-109">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="591f1-109">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="591f1-110">Déplacer vers \< *lecteur*> \ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\\.</span><span class="sxs-lookup"><span data-stu-id="591f1-110">Move to \<*drive*>\ Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK\\.</span></span>  
  
3.  <span data-ttu-id="591f1-111">À l’invite de commandes, tapez **BtarnConfig**, tapez les commutateurs appropriés, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="591f1-111">At the command prompt, type **BtarnConfig**, type the appropriate switches, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="591f1-112">La section suivante décrit les commutateurs.</span><span class="sxs-lookup"><span data-stu-id="591f1-112">The following section describes the switches.</span></span>  
  
## <a name="syntax-for-btarnconfig"></a><span data-ttu-id="591f1-113">Syntaxe de BtarnConfig</span><span class="sxs-lookup"><span data-stu-id="591f1-113">Syntax for BtarnConfig</span></span>  
 <span data-ttu-id="591f1-114">Voici la syntaxe que vous utilisez pour démarrer cet outil de ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="591f1-114">The following shows the syntax that you use to start this command-line tool:</span></span>  
  
### <a name="syntax-for-importing-configuration-data"></a><span data-ttu-id="591f1-115">Syntaxe pour l’importation de données de Configuration</span><span class="sxs-lookup"><span data-stu-id="591f1-115">Syntax for Importing Configuration Data</span></span>  
  
```  
BTARNCONFIG /IMPORT <filename>.xml [/H] [/P] [/R] [/A]  
```  
  
### <a name="syntax-for-exporting-configuration-data"></a><span data-ttu-id="591f1-116">Syntaxe pour l’exportation des données de Configuration</span><span class="sxs-lookup"><span data-stu-id="591f1-116">Syntax for Exporting Configuration Data</span></span>  
  
```  
BTARNCONFIG /EXPORT <filename>.xml [/H] [/P] [/R] [/A]  
```  
  
### <a name="syntax-description"></a><span data-ttu-id="591f1-117">Description de la syntaxe</span><span class="sxs-lookup"><span data-stu-id="591f1-117">Syntax Description</span></span>  
 <span data-ttu-id="591f1-118">Le tableau suivant décrit chaque partie de la syntaxe utilisée par l’utilitaire BtarnConfig.</span><span class="sxs-lookup"><span data-stu-id="591f1-118">The following table describes each part of the syntax that the BtarnConfig utility uses.</span></span>  
  
|<span data-ttu-id="591f1-119">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="591f1-119">Syntax</span></span>|<span data-ttu-id="591f1-120"> Description</span><span class="sxs-lookup"><span data-stu-id="591f1-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="591f1-121">\<*nom de fichier*.xml ></span><span class="sxs-lookup"><span data-stu-id="591f1-121">\<*filename*.xml></span></span>|<span data-ttu-id="591f1-122">Chemin d’accès complet du fichier à importer ou exporter à partir de.</span><span class="sxs-lookup"><span data-stu-id="591f1-122">Full path of the file to import into or export from.</span></span> <span data-ttu-id="591f1-123">Si vous ne fournissez pas un chemin d’accès, BTARN suppose que le chemin d’accès est \< *lecteur*> \ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK.</span><span class="sxs-lookup"><span data-stu-id="591f1-123">If you do not provide a path, BTARN assumes that the path is \<*drive*>\ Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK.</span></span>|  
|<span data-ttu-id="591f1-124">**/ IMPORTATION**</span><span class="sxs-lookup"><span data-stu-id="591f1-124">**/IMPORT**</span></span>|<span data-ttu-id="591f1-125">Importe les données XML à partir de \< *nom de fichier*.xml > dans la configuration de BTARN.</span><span class="sxs-lookup"><span data-stu-id="591f1-125">Imports the XML data from \<*filename*.xml> into the BTARN configuration.</span></span>|  
|<span data-ttu-id="591f1-126">**/ EXPORT**</span><span class="sxs-lookup"><span data-stu-id="591f1-126">**/EXPORT**</span></span>|<span data-ttu-id="591f1-127">Exporte la configuration de BTARN en tant que données XML dans \< *nom de fichier*.xml >.</span><span class="sxs-lookup"><span data-stu-id="591f1-127">Exports the BTARN configuration as XML data into \<*filename*.xml>.</span></span>|  
|<span data-ttu-id="591f1-128">**/H**</span><span class="sxs-lookup"><span data-stu-id="591f1-128">**/H**</span></span>|<span data-ttu-id="591f1-129">Importe ou exporte les données de configuration de l’organisation d’origine.</span><span class="sxs-lookup"><span data-stu-id="591f1-129">Imports or exports home-organization configuration data.</span></span>|  
|<span data-ttu-id="591f1-130">**/P**</span><span class="sxs-lookup"><span data-stu-id="591f1-130">**/P**</span></span>|<span data-ttu-id="591f1-131">Importe ou exporte les données de configuration de serveur partenaire.</span><span class="sxs-lookup"><span data-stu-id="591f1-131">Imports or exports partner configuration data.</span></span>|  
|<span data-ttu-id="591f1-132">**/R**</span><span class="sxs-lookup"><span data-stu-id="591f1-132">**/R**</span></span>|<span data-ttu-id="591f1-133">Importe ou exporte les données de configuration de processus.</span><span class="sxs-lookup"><span data-stu-id="591f1-133">Imports or exports process configuration data.</span></span>|  
|<span data-ttu-id="591f1-134">**/A**</span><span class="sxs-lookup"><span data-stu-id="591f1-134">**/A**</span></span>|<span data-ttu-id="591f1-135">Importe ou exporte les données de configuration d’accord.</span><span class="sxs-lookup"><span data-stu-id="591f1-135">Imports or exports agreement configuration data.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="591f1-136">Notes</span><span class="sxs-lookup"><span data-stu-id="591f1-136">Remarks</span></span>  
 <span data-ttu-id="591f1-137">Si vous ne fournissez pas l’un de le **/H**, **/P**, **/R**, ou **/A** bascule, la BtarnConfig utilitaire importe ou exporte toutes les données.</span><span class="sxs-lookup"><span data-stu-id="591f1-137">If you do not provide any one of the **/H**, **/P**, **/R**, or **/A** switches, the BtarnConfig utility imports or exports all the data.</span></span> <span data-ttu-id="591f1-138">Lorsque vous exportez toutes les données en une seule opération, BtarnConfig exporte les données dans le fichier XML dans l’ordre suivant : accueil organisations, partenaires, la configuration du processus et des accords.</span><span class="sxs-lookup"><span data-stu-id="591f1-138">When you export all the data in one operation, BtarnConfig exports the data into the XML file in the following order: home organizations, partners, process configuration, and agreements.</span></span>  
  
 <span data-ttu-id="591f1-139">S’il existe un problème de structure avec le fichier que vous importez à partir de, BTARN va détecter l’erreur lors de l’étape de validation de schéma, et l’opération échoue avant l’importation de toutes les données.</span><span class="sxs-lookup"><span data-stu-id="591f1-139">If there is a structural problem with the file that you are importing from, BTARN will detect the error during the schema validation stage, and the operation will fail before any data is imported.</span></span> <span data-ttu-id="591f1-140">Si une autre erreur se produit, par exemple, vous essayez d’importer un artefact en double ou HTTPS est requis pour le PIP/de contrat, puis l’opération d’importation échoue.</span><span class="sxs-lookup"><span data-stu-id="591f1-140">If another error occurs, for example, you are trying to import a duplicate artifact or HTTPS is required for the PIP/agreement, then the import operation will fail.</span></span> <span data-ttu-id="591f1-141">Toutefois, toutes les données importées jusqu'à seront conservés dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="591f1-141">However, all the data imported up to that point will remain in the configuration.</span></span>  
  
 <span data-ttu-id="591f1-142">Vous devez être un administrateur BizTalk pour importer ou exporter des données de configuration à l’aide de BtarnConfig.</span><span class="sxs-lookup"><span data-stu-id="591f1-142">You must be a BizTalk administrator to import or export configuration data using BtarnConfig.</span></span> <span data-ttu-id="591f1-143">Si vous n’êtes pas un administrateur BizTalk, certaines opérations d’importation peuvent échouer en raison de problèmes d’accès.</span><span class="sxs-lookup"><span data-stu-id="591f1-143">If you are not a BizTalk administrator, some import operations may fail because of access issues.</span></span> <span data-ttu-id="591f1-144">Toutefois, les autres opérations d’importation dans la même commande BtarnConfig peuvent réussir.</span><span class="sxs-lookup"><span data-stu-id="591f1-144">However,  other import operations in the same BtarnConfig command may succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="591f1-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="591f1-145">See Also</span></span>  
 [<span data-ttu-id="591f1-146">Utilitaires</span><span class="sxs-lookup"><span data-stu-id="591f1-146">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)