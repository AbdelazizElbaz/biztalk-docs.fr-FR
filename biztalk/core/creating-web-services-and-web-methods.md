---
title: "Création de Services Web et méthodes Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, publishing
- Web services, schemas
- orchestrations, naming conventions
- Web services, naming conventions
- schemas, Web services
ms.assetid: a7c47000-501c-47b1-bafa-82370585c1db
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74065489e427ae0612897f1f333e3c8e154a535f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-web-services-and-web-methods"></a><span data-ttu-id="5a1bd-102">Création de Services Web et méthodes Web</span><span class="sxs-lookup"><span data-stu-id="5a1bd-102">Creating Web Services and Web Methods</span></span>
<span data-ttu-id="5a1bd-103">Lorsque vous publiez des schémas en tant que service Web, vous contrôlez la création de services et de méthodes Web dans l'Assistant Publication de services Web BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-103">When you publish schemas as a Web service, you control the creation of Web services and Web methods in the BizTalk Web Services Publishing Wizard.</span></span> <span data-ttu-id="5a1bd-104">Vous pouvez renommer la description du service Web, le service Web et la méthode Web à l'intérieur de l'arborescence disponible sur la page des services Web.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-104">You can rename the Web service description, Web service and Web method inside the tree available on the Web Services page.</span></span> <span data-ttu-id="5a1bd-105">Vous pouvez ajouter et supprimer des services et des méthodes Web.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-105">You can add and remove Web services and Web methods.</span></span> <span data-ttu-id="5a1bd-106">L'Assistant utilise les noms d'élément racines des schémas de demande sélectionnés comme noms de paramètre d'entrée.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-106">The wizard uses the root element names of the selected request schemas as the input parameter name.</span></span> <span data-ttu-id="5a1bd-107">La valeur de retour de la méthode Web renvoie le schéma de réponse.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-107">The Web method return value returns the response schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a1bd-108">Les clients Web ASP.NET peuvent changer la signature de la méthode Web en combinant les paramètres d'entrée et de sortie du même type.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-108">ASP.NET Web clients may change the Web method signature by combining the in and out parameters of the same type.</span></span> <span data-ttu-id="5a1bd-109">Par exemple, un client Web ASP.NET peut changer une méthode BizTalk Web à partir de **string myService (partie de la chaîne)** à **void myService (partie de la chaîne ref)**.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-109">For example, an ASP.NET Web client may change a BizTalk Web method from **string myService(string part)** to **void myService(ref string part)**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a1bd-110">Si votre réception port est défini en tant qu’unidirectionnel, le type de réponse de la méthode Web est **void** et aucune information n’est retournée au client Web.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-110">If your receive port is defined as one-way, the Web method response type is **void** and no information is returned to the Web client.</span></span> <span data-ttu-id="5a1bd-111">L'adaptateur SOAP et l'orchestration ne renvoient pas d'exceptions levées au client Web.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-111">The SOAP adapter and orchestration do not return thrown exceptions to the Web client.</span></span>  
  
## <a name="web-services-naming-conventions-for-published-orchestrations"></a><span data-ttu-id="5a1bd-112">Conventions d'affectation de noms des services Web pour les orchestrations publiées</span><span class="sxs-lookup"><span data-stu-id="5a1bd-112">Web services naming conventions for published orchestrations</span></span>  
 <span data-ttu-id="5a1bd-113">L'Assistant Publication de services Web BizTalk génère des noms de fichier de service Web (.asmx) basés sur la description des services Web que vous définissez dans la page de service Web.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-113">The BizTalk Web Services Publishing Wizard generates Web service (.asmx) file names based on the Web services description that you define in the Web Service page.</span></span> <span data-ttu-id="5a1bd-114">Le tableau suivant affiche les valeurs par défaut pour les noms de fichier de service Web.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-114">The following table shows the default values for the Web service file names.</span></span>  
  
|<span data-ttu-id="5a1bd-115">Service Web généré</span><span class="sxs-lookup"><span data-stu-id="5a1bd-115">Generated Web service</span></span>|<span data-ttu-id="5a1bd-116">Nom de fichier</span><span class="sxs-lookup"><span data-stu-id="5a1bd-116">File name</span></span>|  
|---------------------------|---------------|  
|<span data-ttu-id="5a1bd-117">BizTalkWebService</span><span class="sxs-lookup"><span data-stu-id="5a1bd-117">BizTalkWebService</span></span>|<span data-ttu-id="5a1bd-118">Nom du projet de service Web Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5a1bd-118">Visual Studio Web Service project name</span></span>|  
|<span data-ttu-id="5a1bd-119">WebService1</span><span class="sxs-lookup"><span data-stu-id="5a1bd-119">WebService1</span></span>|<span data-ttu-id="5a1bd-120">Nom de fichier du service Web (.asmx)</span><span class="sxs-lookup"><span data-stu-id="5a1bd-120">Web service (.asmx) file name</span></span>|  
|<span data-ttu-id="5a1bd-121">WebMethod1</span><span class="sxs-lookup"><span data-stu-id="5a1bd-121">WebMethod1</span></span>|<span data-ttu-id="5a1bd-122">Nom de méthode Web</span><span class="sxs-lookup"><span data-stu-id="5a1bd-122">Web method name</span></span>|  
  
 <span data-ttu-id="5a1bd-123">Le service Web généré ne reflète pas les noms des nœuds restants.</span><span class="sxs-lookup"><span data-stu-id="5a1bd-123">The generated Web service does not reflect the names of the remaining nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a1bd-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a1bd-124">See Also</span></span>  
 <span data-ttu-id="5a1bd-125">[Publication de schémas comme un Service Web](../core/publishing-schemas-as-a-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="5a1bd-125">[Publishing Schemas as a Web Service](../core/publishing-schemas-as-a-web-service.md) </span></span>  
 [<span data-ttu-id="5a1bd-126">Comment utiliser l’Assistant Publication de Services Web BizTalk pour publier des schémas en tant qu’un Service Web</span><span class="sxs-lookup"><span data-stu-id="5a1bd-126">How to Use the BizTalk Web Services Publishing Wizard to Publish Schemas as a Web Service</span></span>](../core/publish-schemas-as-web-services-with-biztalk-web-services-publishing-wizard.md)