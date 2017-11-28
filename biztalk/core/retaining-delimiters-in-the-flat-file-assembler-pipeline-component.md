---
title: "Conservation des délimiteurs dans le composant de Pipeline assembleur fichier plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adc27561-9996-49a9-b715-e313b9148506
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9d10879adfbe0ca0c68376faa48d9976fc19599
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="retaining-delimiters-in-the-flat-file-assembler-pipeline-component"></a><span data-ttu-id="1a450-102">Conservation des délimiteurs dans le composant de pipeline Assembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="1a450-102">Retaining Delimiters in the Flat File Assembler Pipeline Component</span></span>
<span data-ttu-id="1a450-103">En cas d'enregistrements manquants dans le message acheminé via un pipeline personnalisé utilisant l'Assembleur de fichier plat, le délimiteur de ces enregistrements peut ou peut ne pas apparaître dans la sortie du fichier plat selon l'emplacement dans le fichier d'entrée où les enregistrements manquent.</span><span class="sxs-lookup"><span data-stu-id="1a450-103">If there are missing records in the message going through a custom pipeline that uses the Flat File Assembler, the delimiter for those records may or may not appear in the flat file output depending on where in the input file the records are missing.</span></span>  
  
 <span data-ttu-id="1a450-104">Pour que le fichier plat conserve certains délimiteurs, vous pouvez utiliser un mappage et un script personnalisé afin de vous assurer qu'un enregistrement « vide » sera créé lorsqu'un enregistrement d'entrée spécifique n'existera pas dans le message.</span><span class="sxs-lookup"><span data-stu-id="1a450-104">To ensure that the flat file retain certain delimiters, you can use a map and a custom script to make sure an "empty" record is created when a specific input record does not exist in the message.</span></span> <span data-ttu-id="1a450-105">Pour que cela fonctionne, vous devez vérifier que les nœuds potentiellement vides dans le schéma de document pour l'Assembleur de fichier plat disposent des propriétés suivantes définies comme suit :</span><span class="sxs-lookup"><span data-stu-id="1a450-105">For this to work, you must make sure that the potentially empty nodes in the document schema for the Flat File Assembler have the following properties set as shown:</span></span>  
  
|<span data-ttu-id="1a450-106">Propriété</span><span class="sxs-lookup"><span data-stu-id="1a450-106">Property</span></span>|<span data-ttu-id="1a450-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="1a450-107">Setting</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="1a450-108">Préserver le délimiteur pour les données vides</span><span class="sxs-lookup"><span data-stu-id="1a450-108">Preserve Delimiter for Empty Data</span></span>|<span data-ttu-id="1a450-109">Oui</span><span class="sxs-lookup"><span data-stu-id="1a450-109">Yes</span></span>|  
|<span data-ttu-id="1a450-110">Supprimer les délimiteurs de fin</span><span class="sxs-lookup"><span data-stu-id="1a450-110">Suppress Trailing Delimiters</span></span>|<span data-ttu-id="1a450-111">Non</span><span class="sxs-lookup"><span data-stu-id="1a450-111">No</span></span>|  
|<span data-ttu-id="1a450-112">Générer les nœuds vides (définissez cette propriété sur le nœud racine)</span><span class="sxs-lookup"><span data-stu-id="1a450-112">Generate Empty Nodes (set this on the root node)</span></span>|<span data-ttu-id="1a450-113">True</span><span class="sxs-lookup"><span data-stu-id="1a450-113">True</span></span>|  
  
### <a name="to-create-a-map-that-creates-an-empty-record"></a><span data-ttu-id="1a450-114">Pour créer un mappage qui génère un enregistrement « vide »</span><span class="sxs-lookup"><span data-stu-id="1a450-114">To create a map that creates an "empty" record</span></span>  
  
1.  <span data-ttu-id="1a450-115">Ajoutez un nouveau mappage à votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1a450-115">Add a new map to your BizTalk project.</span></span>  
  
2.  <span data-ttu-id="1a450-116">Spécifiez le schéma de document utilisé par l'Assembleur de fichier plat, à la fois en tant que source de mappage et schéma de destination du mappage.</span><span class="sxs-lookup"><span data-stu-id="1a450-116">Specify the document schema used by the Flat File Assembler as both the map source and map destination schema.</span></span>  
  
3.  <span data-ttu-id="1a450-117">Mappez les champs sources qui ne seront pas vides aux champs de destination correspondants.</span><span class="sxs-lookup"><span data-stu-id="1a450-117">Map the source fields that will not be empty to the corresponding destination fields.</span></span>  
  
4.  <span data-ttu-id="1a450-118">Pour les champs qui peuvent être vides, utiliser un script personnalisé pour vérifier si le champ source est vide et retourner une chaîne vide (au lieu de Nil).</span><span class="sxs-lookup"><span data-stu-id="1a450-118">For those fields that may be empty, use a custom script to check if the source field is empty and return an empty string (instead of Nil).</span></span> <span data-ttu-id="1a450-119">Utilisez un script similaire à celui indiqué ci-après :</span><span class="sxs-lookup"><span data-stu-id="1a450-119">Use a script like the following:</span></span>  
  
    ```  
    public string ValOrEmpty(string val)  
    {  
         return (val.Length > 0) ? val : "";  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1a450-120">Vous devez créer un script avec un nom de fonction unique pour chaque champ potentiellement vide que vous mappez.</span><span class="sxs-lookup"><span data-stu-id="1a450-120">You must create a script with a unique function name for each potentially empty field you map.</span></span> <span data-ttu-id="1a450-121">Par exemple, si trois champs peuvent être vides, vous aurez les fonctions `ValOrEmpty1`, `ValOrEmpty2`, `ValOrEmpty3`.</span><span class="sxs-lookup"><span data-stu-id="1a450-121">For example, if you have three fields that may be empty, you might have functions named `ValOrEmpty1`, `ValOrEmpty2`, `ValOrEmpty3`.</span></span>  
  
5.  <span data-ttu-id="1a450-122">À l’aide de la console d’Administration de BizTalk Server, de configurer le port d’envoi avec le pipeline personnalisé et le composant Assembleur de fichier plat à utiliser la carte en tant qu’un mappage sortant.</span><span class="sxs-lookup"><span data-stu-id="1a450-122">Using BizTalk Server Administration console, configure the send port with the custom pipeline and flat file assembler component to use the map as an outbound map.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a450-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a450-123">See Also</span></span>  
 <span data-ttu-id="1a450-124">[Comment configurer les mappages sortants pour un Port d’envoi](../core/how-to-configure-outbound-maps-for-a-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="1a450-124">[How to Configure Outbound Maps for a Send Port](../core/how-to-configure-outbound-maps-for-a-send-port.md) </span></span>  
 [<span data-ttu-id="1a450-125">Composant de Pipeline assembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="1a450-125">Flat File Assembler Pipeline Component</span></span>](../core/flat-file-assembler-pipeline-component.md)