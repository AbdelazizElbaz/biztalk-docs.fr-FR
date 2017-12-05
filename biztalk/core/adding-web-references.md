---
title: "Ajout de références Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BPEL, orchestrations
- orchestrations, BPEL
- Web services, ports
- orchestrations, exporting
- Web services, projects
- Web services, references
- projects, Web services
ms.assetid: 7e40f215-f11a-4151-bcc6-e107bf36b6f6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cbf8cd4c21009190fc459312467656410dc663a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="adding-web-references"></a><span data-ttu-id="75b48-102">Ajout de références web</span><span class="sxs-lookup"><span data-stu-id="75b48-102">Adding Web References</span></span>
<span data-ttu-id="75b48-103">Avant de pouvoir ajouter un port Web, vous devez ajouter une référence Web à votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="75b48-103">Before you can add a Web port, you need to add a Web reference to your BizTalk project.</span></span> <span data-ttu-id="75b48-104">Une référence Web est une description d'un service Web qui est disponible pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="75b48-104">A Web reference is a description of a Web service that is available to your project.</span></span> <span data-ttu-id="75b48-105">Lorsque vous ajoutez une référence Web à votre projet, le projet BizTalk crée une orchestration Web type de port, les types de messages Web Reference.map (fichier de mappage), Reference.odx (fichier d’orchestration), \< *WebService*\>. disco (fichier de découverte) et \< *WebService*\>.wsdl (fichier Web Service Description Language) à votre projet.</span><span class="sxs-lookup"><span data-stu-id="75b48-105">When you add a Web reference to your project, BizTalk project creates an orchestration Web port type, Web message types, Reference.map (map file), Reference.odx (orchestration file), \<*WebService*\>.disco (discovery file), and \<*WebService*\>.wsdl (Web Service Description Language file) to your project.</span></span> <span data-ttu-id="75b48-106">Si le fichier WSDL contient des types de messages Web de schéma, le projet BizTalk ajoute Reference.xsd à votre projet.</span><span class="sxs-lookup"><span data-stu-id="75b48-106">If your Web Service Description Language (WSDL) file contains schema Web message types, BizTalk project adds Reference.xsd to your project.</span></span>  
  
 <span data-ttu-id="75b48-107">Une référence Web inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="75b48-107">A Web reference includes:</span></span>  
  
-   <span data-ttu-id="75b48-108">une URL (Uniform Resource Locator) pour le service Web ;</span><span class="sxs-lookup"><span data-stu-id="75b48-108">A Universal Resource Locator (URL) for the Web service.</span></span>  
  
-   <span data-ttu-id="75b48-109">un fichier WSDL qui contient des informations sur le service, telles que les méthodes, ports et types de messages disponibles ;</span><span class="sxs-lookup"><span data-stu-id="75b48-109">A WSDL file that offers information about the service such as available methods, ports, and message types.</span></span>  
  
-   <span data-ttu-id="75b48-110">un mappage de référence (Reference.map).</span><span class="sxs-lookup"><span data-stu-id="75b48-110">A reference map (Reference.map).</span></span>  
  
 <span data-ttu-id="75b48-111">Lorsque vous ajoutez une référence Web, toutes les méthodes Web pour ce service Web doivent être compatibles avec BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="75b48-111">When you add a Web reference, all the Web methods for that Web service must be compatible with BizTalk Server.</span></span> <span data-ttu-id="75b48-112">Il est impossible de spécifier des attributs conditionnels pour des méthodes Web spécifiques dans un service Web.</span><span class="sxs-lookup"><span data-stu-id="75b48-112">You cannot specify conditional attributes for specific Web methods in a Web service.</span></span>  
  
 <span data-ttu-id="75b48-113">Vous ajoutez une référence Web à votre projet à l’aide de la **ajouter une référence Web** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="75b48-113">You add a Web reference to your project by using the **Add Web Reference** dialog box.</span></span> <span data-ttu-id="75b48-114">Pour plus d’informations sur l’ajout de références Web, consultez [à l’aide de Visual Studio](../core/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="75b48-114">For more information about adding Web references, see [Using Visual Studio](../core/using-visual-studio.md).</span></span>  
  
 <span data-ttu-id="75b48-115">Si vous envisagez d'exporter votre orchestration à l'aide du processus d'exportation BPEL (Business Process Execution Language), vous ne pouvez pas référencer une référence Web d'un projet existant.</span><span class="sxs-lookup"><span data-stu-id="75b48-115">If you are planning to export your orchestration using the Business Process Execution Language (BPEL) export process, you cannot reference a Web reference from an existing BizTalk project.</span></span> <span data-ttu-id="75b48-116">Si vous effectuez cette opération, le processus d'exportation BPEL génère automatiquement un second fichier WSDL et vous perdez vos informations de liaison.</span><span class="sxs-lookup"><span data-stu-id="75b48-116">When you reference a Web reference from an existing BizTalk project, the BPEL export process will auto-generate a second WSDL file and you will lose your binding information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b48-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75b48-117">See Also</span></span>  
 <span data-ttu-id="75b48-118">[Création de Ports Web](../core/creating-web-ports.md) </span><span class="sxs-lookup"><span data-stu-id="75b48-118">[Creating Web Ports](../core/creating-web-ports.md) </span></span>  
 [<span data-ttu-id="75b48-119">Consommation des services web</span><span class="sxs-lookup"><span data-stu-id="75b48-119">Consuming Web Services</span></span>](../core/consuming-web-services.md)