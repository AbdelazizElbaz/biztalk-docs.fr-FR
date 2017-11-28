---
title: "Interface IStaticAdapterConfig de l’adaptateur statique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f5de01-0cfc-456a-a52b-28f8f076bdfc
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de8d95ba4a5945cb43e3681055750cdad628759
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="static-adapter-istaticadapterconfig-interface"></a><span data-ttu-id="7ff01-102">Interface IStaticAdapterConfig de l'adaptateur statique</span><span class="sxs-lookup"><span data-stu-id="7ff01-102">Static Adapter IStaticAdapterConfig Interface</span></span>
<span data-ttu-id="7ff01-103">Un adaptateur de conception statique doit implémenter la **IStaticAdapterConfig** interface.</span><span class="sxs-lookup"><span data-stu-id="7ff01-103">A static design-time adapter must implement the **IStaticAdapterConfig** interface.</span></span> <span data-ttu-id="7ff01-104">Celle-ci lui permet de communiquer avec l'Assistant Ajouter les métadonnées de l'adaptateur et d'obtenir des organisations de service et des descriptions de service individuel à partir de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7ff01-104">This allows it to interact with the Add Adapter Metadata Wizard and obtain service organizations and individual service descriptions from the adapter.</span></span> <span data-ttu-id="7ff01-105">L’Assistant appelle les **GetServiceOrganization** et **GetServiceDescription** de projet dans les méthodes pour extraire des informations de métadonnées avec lequel l’adaptateur interagit et l’ajouter à un BizTalk [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ff01-105">The wizard calls the **GetServiceOrganization** and **GetServiceDescription** methods to pull in metadata information with which the adapter interacts and add it to a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7ff01-106">Le **GetServiceOrganization** méthode obtient une instance de document XML qui représente l’organisation hiérarchique des services exposés de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7ff01-106">The **GetServiceOrganization** method obtains an XML instance document that represents the hierarchical organization of the adapter's exposed services.</span></span> <span data-ttu-id="7ff01-107">Cette structure génère l’arborescence d’organisation de service que vous voyez sur le **sélectionner les Services à importer** page de l’Assistant Ajout de métadonnées d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7ff01-107">This structure generates the service organization tree that you see on the **Select Services to Import** page in the Add Adapter Metadata Wizard.</span></span>  
  
 <span data-ttu-id="7ff01-108">Après avoir sélectionné les services à importer, l’Assistant appelle les **GetServiceDescription** pour obtenir un tableau de fichiers Web Services Description Language (WSDL) correspondant aux catégories de service qui ont été sélectionnés dans la zone Ajouter (méthode) Arborescence de l’Assistant de métadonnées adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7ff01-108">After you select the services to import, the wizard calls the **GetServiceDescription** method to obtain an array of Web Services Description Language (WSDL) files corresponding to the service categories that were selected in the Add Adapter Metadata Wizard tree.</span></span> <span data-ttu-id="7ff01-109">Les schémas représentant les services sont créés en tant que fichiers XSD et sont ajoutés à votre projet BizTalk une fois que vous avez terminé l'Assistant Ajouter les métadonnées de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7ff01-109">Schemas representing the services are generated as XSD files and added to your BizTalk project after you complete the Add Adapter Metadata Wizard.</span></span>  
  
 <span data-ttu-id="7ff01-110">Dans l’exemple d’adaptateur de fichier, le **GetServiceOrganization** et **GetServiceDescription** méthodes se trouvent dans le **StaticAdapterManagement** classe dans le Fichier de classe AdapterManagement.cs.</span><span class="sxs-lookup"><span data-stu-id="7ff01-110">In the file adapter sample, the **GetServiceOrganization** and **GetServiceDescription** methods reside in the **StaticAdapterManagement** class in the AdapterManagement.cs class file.</span></span> <span data-ttu-id="7ff01-111">L’Assistant appelle les **GetServiceOrganization** méthode pour obtenir la structure arborescente à afficher sur le **sélectionner les Services à importer** page.</span><span class="sxs-lookup"><span data-stu-id="7ff01-111">The wizard calls the **GetServiceOrganization** method to obtain the tree structure to display on the **Select Services to Import** page.</span></span> <span data-ttu-id="7ff01-112">Dans **GetServicesOrganization** le codé en dur retourne la valeur du fichier AdapterManagement.CategorySchema.xml est utilisée comme indiqué dans le fragment de code suivant.</span><span class="sxs-lookup"><span data-stu-id="7ff01-112">In **GetServicesOrganization** the hard-coded return value of AdapterManagement.CategorySchema.xml file is used as shown in the following code fragment.</span></span> <span data-ttu-id="7ff01-113">En tant que développeur d'adaptateur, vous devrez ajouter la logique pour renvoyer le fichier XML approprié.</span><span class="sxs-lookup"><span data-stu-id="7ff01-113">As an adapter developer you will need to add the logic to return the appropriate XML file.</span></span>  
  
```  
public string GetServiceOrganization(IPropertyBag endPointConfiguration, string NodeIdentifier)   
{  
   string result = GetResource("AdapterManagement.CategorySchema.xml");  
   return result;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="7ff01-114">Assurez-vous de modifier le **GetServiceDescription** méthode de la **StaticAdapterManagement** (classe) et non de la **DynamicAdapterManagement** (classe), qui apparaît en premier dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="7ff01-114">Be sure to modify the **GetServiceDescription** method of the **StaticAdapterManagement** class, and not of the **DynamicAdapterManagement** class, which appears first in the file.</span></span>  
  
 <span data-ttu-id="7ff01-115">Le code suivant est issu le **GetServiceDescription** méthode du fichier AdapterManagement.cs.</span><span class="sxs-lookup"><span data-stu-id="7ff01-115">The following code is from the **GetServiceDescription** method of the AdapterManagement.cs file.</span></span> <span data-ttu-id="7ff01-116">Le fichier service1.wsdl est codé en dur en tant que fichier WSDL renvoyé.</span><span class="sxs-lookup"><span data-stu-id="7ff01-116">The file service1.wsdl is hard-coded as the WSDL file returned.</span></span> <span data-ttu-id="7ff01-117">Il renvoie des schémas représentés en tant que fichiers WSDL.</span><span class="sxs-lookup"><span data-stu-id="7ff01-117">It returns schemas represented as WSDL files.</span></span> <span data-ttu-id="7ff01-118">Le `wsdls` paramètre est un tableau de références WSDL uniques qui correspondent aux références WSDL dans le XML source chargé par **GetServicesOrganization**.</span><span class="sxs-lookup"><span data-stu-id="7ff01-118">The `wsdls` parameter is an array of unique WSDL references that correspond to the WSDL references in the source XML loaded by **GetServicesOrganization**.</span></span> <span data-ttu-id="7ff01-119">Le jeu de descriptions WSDL retourné est utilisé pour générer les types de port et les types de messages pour le projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7ff01-119">The returned set of WSDL descriptions are used to generate the port types and message types for the BizTalk project.</span></span> <span data-ttu-id="7ff01-120">Si plusieurs types de schéma sont sélectionnables dans l'arborescence, plusieurs fichiers WSDL sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="7ff01-120">If you have more than one schema type available for selection in the tree, you will need more than one WSDL file.</span></span> <span data-ttu-id="7ff01-121">Si vous avez le choix entre plusieurs schémas et plusieurs fichiers WSDL, vous pouvez ajouter une consultation de base de données pour garantir le renvoi du fichier WSDL correct.</span><span class="sxs-lookup"><span data-stu-id="7ff01-121">If you have many possible schema and WSDL choices, you may want to add a database lookup to return the correct WSDL file.</span></span>  
  
```  
/// <summary>     
        /// Get the WSDL file name for the selected WSDL  
        /// </summary>  
        /// <param name="wsdls">place holder</param>  
        /// <returns>An empty string[]</returns>  
        public string[] GetServiceDescription(string[] wsdls)   
      {  
            string[] result = new string[1];  
            result[0] = GetResource("AdapterManagement.service1.wsdl");  
            return result;  
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ff01-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ff01-122">See Also</span></span>  
 [<span data-ttu-id="7ff01-123">Configuration de l’adaptateur de conception statique</span><span class="sxs-lookup"><span data-stu-id="7ff01-123">Static Design-Time Adapter Configuration</span></span>](../core/static-design-time-adapter-configuration.md)