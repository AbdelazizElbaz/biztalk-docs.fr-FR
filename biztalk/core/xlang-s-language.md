---
title: Langage XLANG-s | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, properties
ms.assetid: 97b62f17-5a8d-4d87-8563-1f6d941f027f
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2329d4bc42617d70227481a0d70064d368f3c0e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-language"></a><span data-ttu-id="9b0ab-102">Langage XLANG-s</span><span class="sxs-lookup"><span data-stu-id="9b0ab-102">XLANG-s Language</span></span>
<span data-ttu-id="9b0ab-103">XLANG/s a été conçu pour utiliser des normes Internet telles que XML, XSD et WSDL (Web Services Description Language), et dispose d'une prise en charge intégrée permettant d'utiliser des messages et objets NET.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-103">XLANG/s was designed to use Internet standards such as XML, XSD, and Web Services Description Language (WSDL), and has embedded support for working with .NET-based objects and messages.</span></span> <span data-ttu-id="9b0ab-104">XLANG/s peut être considéré comme un langage de messagerie comportant certaines des fonctionnalités d'expression de C#.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-104">XLANG/s can be viewed as a messaging language with some of the expression capabilities of C#.</span></span> <span data-ttu-id="9b0ab-105">Toutefois, le code n'est pas portable entre XLANG/s et C#.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-105">However, code is not portable between XLANG/s and C#.</span></span>  
  
 <span data-ttu-id="9b0ab-106">XLANG/s favorise une séparation claire entre le processus et l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-106">XLANG/s encourages a clear separation between process and implementation.</span></span> <span data-ttu-id="9b0ab-107">Par exemple, le protocole ou processus d'entreprise est spécifié dans XLANG/s, et les aspects locaux de l'application, tels que l'accès aux bases de données, sont implémentés dans d'autres langages de programmation .NET tels que C# ou Visual Basic.NET.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-107">For example, the business process or protocol is specified in XLANG/s, and the local aspects of the application, such as database access, are implemented in other .NET programming languages such as C# or Visual Basic.NET.</span></span>  
  
 <span data-ttu-id="9b0ab-108">La syntaxe d'expression ou d'assignation XLANG/s est modélisée après C#, et vous devez référencer la spécification C# pour obtenir la syntaxe exacte.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-108">XLANG/s assignment and expression syntax is modeled after C#, and you should reference the C# specification for exact syntax.</span></span> <span data-ttu-id="9b0ab-109">XLANG/s définit un ensemble complet de constructions de haut niveau permettant de définir des processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-109">XLANG/s defines a rich set of high-level constructs that are used to define business processes.</span></span> <span data-ttu-id="9b0ab-110">Tandis que XLANG/s prend en charge pour les types de données de bas niveau comme chaîne et entier, les types de données de haut niveau sont également définies : messages, ports, corrélations et liens de service.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-110">While XLANG/s provides support for low-level data types like string and integer, high-level data types are also defined: messages, ports, correlations, and service links.</span></span> <span data-ttu-id="9b0ab-111">Ces données servent à permettent de définir la sémantique associée à un processus d’entreprise types et sont complétés par des processus tels que des instructions de contrôle **pendant** ou **étendue**.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-111">These data types are used to rigorously define the semantics associated with a business process, and are complemented by process control statements such as **while** or **scope**.</span></span>  
  
 <span data-ttu-id="9b0ab-112">Instructions XLANG/s se décomposent généralement en deux catégories : les instructions simples qui agissent sur leurs propres, telles que **réception** ou **envoyer**et des instructions complexes qui contiennent ou regroupent les deux instructions simples ou autres instructions complexes, tels que **étendue**, **parallèles**, et **écouter**.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-112">XLANG/s statements generally fall into one of two categories: simple statements that act on their own, such as **receive** or **send**, and complex statements that contain or group either simple statements or other complex statements, such as **scope**, **parallel**, and **listen**.</span></span> <span data-ttu-id="9b0ab-113">Les sémantiques représentées dans XLANG/s sont une réflexion de celles définies dans la spécification BPEL4WS (Business Process Execution Language for Web Services) publiée par Microsoft, IBM et BEA pour la définition de la sémantique des processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-113">The semantics embodied in XLANG/s are a reflection of those defined in the Business Process Execution Language for Web Services (BPEL4WS) specification published by Microsoft, IBM, and BEA for the definition of business process semantics.</span></span>  
  
 <span data-ttu-id="9b0ab-114">La maîtrise des principales constructions de XLANG/s est facultative car elles sont créées par les diagrammes d'orchestration de dessin dans le Concepteur d'orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-114">Understanding the main constructs of XLANG/s is optional because they are produced as a result of drawing orchestration diagrams in BizTalk Orchestration Designer.</span></span> <span data-ttu-id="9b0ab-115">Le Concepteur d'orchestration est un outil graphique complet permettant de concevoir visuellement des processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-115">Orchestration Designer is a rich graphical tool for visually designing business processes.</span></span> <span data-ttu-id="9b0ab-116">Il génère des fichiers XLANG/s qui ont une extension .odx et contiennent des informations visuelles supplémentaires dans leurs en-têtes, ainsi que des informations sur les attributs personnalisés dans leurs corps.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-116">It generates XLANG/s files that have an .odx extension and contain additional visual information in their headers and custom attribute information in their bodies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b0ab-117">Le langage XLANG/s est propriétaire et n'est pas entièrement documenté.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-117">The XLANG/s language is proprietary and is not fully documented.</span></span> <span data-ttu-id="9b0ab-118">Cette section présente certaines parties de celui-ci pouvant s'avérer nécessaire lorsque vous développez vos orchestrations.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-118">This section exposes certain parts of the language that you might need to be aware of as you develop your orchestrations.</span></span> <span data-ttu-id="9b0ab-119">La modification directe des fichiers .odx n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-119">Direct modification of the .odx files is not supported.</span></span>  
  
## <a name="xlangs-programs"></a><span data-ttu-id="9b0ab-120">Programmes XLANG/s</span><span class="sxs-lookup"><span data-stu-id="9b0ab-120">XLANG/s Programs</span></span>  
 <span data-ttu-id="9b0ab-121">Le programme XLANG/s le plus simple exige qu'un type de message soit défini afin de fournir à l'orchestration les données nécessaires pour démarrer.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-121">The simplest XLANG/s program requires that a message type be defined, which gives the orchestration some data to start to work with.</span></span> <span data-ttu-id="9b0ab-122">L'orchestration reçoit le message sur un port puis se termine.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-122">The orchestration receives the message over a port and then terminates.</span></span> <span data-ttu-id="9b0ab-123">Le code suivant en est un exemple :</span><span class="sxs-lookup"><span data-stu-id="9b0ab-123">The following code is an example:</span></span>  
  
```  
module HelloWorldApp  
{  
     private porttype ptPOReceive  
     {  
      oneway opPOReceive  
      {  
       HelloWorldApp.PurchaseOrder  
      }  
     }  
     private porttype ptPOSend  
     {  
      oneway opPOSend  
      {  
       HelloWorldApp.PurchaseOrder  
      }  
     }  
     private service  HelloWorld  
     {  
      port implements HelloWorldApp.ptPOReceive poPOReceive;  
      port uses HelloWorldApp.ptPOSend poPOSend;  
      message HelloWorldApp.PurchaseOrder msgPO;  
      body ()  
      {  
       activate receive (poPOReceive.opPOReceive, msgPO);  
       send (poPOSend.opPOSend, msgPO);  
       }  
     }  
}  
```  
  
 <span data-ttu-id="9b0ab-124">Dans le programme XLANG/s précédent, le mot clé `module` définit l'unité de compilation d'un programme XLANG/s.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-124">In the preceding XLANG/s program, the `module` keyword defines the unit of compilations for an XLANG/s program.</span></span> <span data-ttu-id="9b0ab-125">Tous les types utilisés dans le programme, tel que **porttype**, **correlationsettype**, **servicelinktype**, et **messagetype**— sont limités à Ce niveau.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-125">All types used in the program—such as **porttype**, **correlationsettype**, **servicelinktype**, and **messagetype**—are scoped at this level.</span></span>  
  
 <span data-ttu-id="9b0ab-126">Un port est une construction qui XLANG/s peut envoyer ou recevoir des messages à partir d’ou et le port a un type défini appelé **porttype**.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-126">A port is a construct that XLANG/s can send or receive messages to or from, and the port has a defined type called **porttype**.</span></span> <span data-ttu-id="9b0ab-127">Le **porttype** construction définit une collection d’opérations qui peuvent être utilisées sur le port.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-127">The **porttype** construct defines a collection of operations that can be used on the port.</span></span> <span data-ttu-id="9b0ab-128">Ces opérations définissent un échange de message valide unique sur le port.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-128">These operations define a single valid message exchange over the port.</span></span> <span data-ttu-id="9b0ab-129">Dans la définition **porttype**, **messagetype**, **servicelinktype**, ou **correlationsettype** construit, l’auteur de XLANG/s programme consiste essentiellement à créer les définitions de type de données complexes.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-129">In defining **porttype**, **messagetype**, **servicelinktype**, or **correlationsettype** constructs, the author of an XLANG/s program is essentially creating complex data type definitions.</span></span> <span data-ttu-id="9b0ab-130">Ces définitions présentent les mêmes avantages comme types de données complexes dans d’autres langages : ils extraient les notions représentées dans le type de données à un niveau supérieur, et permettent de réutiliser facilement le type de données.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-130">These definitions have the same advantages as complex data types do in other languages: They abstract the notions embodied in the data type to a higher level, and they allow for easy reuse of the data type.</span></span>  
  
 <span data-ttu-id="9b0ab-131">Le **ptPOReceive** opération de port de réception port helloworldapp précédent module est défini avec un unidirectionnel **opPOReceive**.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-131">The **ptPOReceive** port in the preceding HelloWorldApp module is defined with a one-way receive port operation, **opPOReceive**.</span></span> <span data-ttu-id="9b0ab-132">Le bloc HelloWorld de service définit l'implémentation réelle du processus et les variables utilisables, dont celles de port et de message.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-132">The service HelloWorld block defines the actual implementation of the process and any variables it may use, including port and message variables.</span></span> <span data-ttu-id="9b0ab-133">Les trois premières lignes de code dans ce bloc définissent les variables de port **poPOReceive** et **poPOSend** et le message **msgPO** respectivement.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-133">The first three lines of code within this block define the port variables **poPOReceive** and **poPOSend** and the message **msgPO** respectively.</span></span> <span data-ttu-id="9b0ab-134">Le corps contient le code décrivant les paramètres du service et du comportement d'exécution.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-134">The body contains the code describing parameters to the service and the execution behavior.</span></span> <span data-ttu-id="9b0ab-135">Toutes les variables, à l'exception de celles définies avec un bloc d'étendues imbriquées, sont étendues à ce niveau.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-135">All variables, unless defined with a nested scope block, are scoped to this level.</span></span> <span data-ttu-id="9b0ab-136">L’instruction receive, qui est une réception avec activation, reçoit la **msgPO** message à partir de la **poPOReceive.opPOReceive** de port et crée une nouvelle instance de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-136">The receive statement, which is an activate receive, receives the **msgPO** message from the **poPOReceive.opPOReceive** port and creates a new instance of the orchestration.</span></span> <span data-ttu-id="9b0ab-137">Une fois le message reçu, l'instruction d'envoi dirige le message vers un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-137">After the message is received, the send statement directs the message to a send port.</span></span> <span data-ttu-id="9b0ab-138">Dans les deux déclarations de port dans le code précédent, **poPOReceive** utilise le modificateur d’implémentation, tandis que **poPOSend** utilise le modificateur d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-138">In the two port declarations in the preceding code, **poPOReceive** uses the implements modifier, whereas **poPOSend** uses the uses modifier.</span></span> <span data-ttu-id="9b0ab-139">Le modificateur d'implémentation indique au runtime qu'il recevra un message sur ce port.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-139">The implements modifier tells the runtime it will be receiving a message over that port.</span></span> <span data-ttu-id="9b0ab-140">Le modificateur d'utilisation indique au runtime qu'il enverra un message sur ce port.</span><span class="sxs-lookup"><span data-stu-id="9b0ab-140">The uses modifier tells the runtime that it will be sending a message over that port.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b0ab-141">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9b0ab-141">In This Section</span></span>  
  
-   [<span data-ttu-id="9b0ab-142">Types de données XLANG-s</span><span class="sxs-lookup"><span data-stu-id="9b0ab-142">XLANG-s Data Types</span></span>](../core/xlang-s-data-types.md)  
  
-   [<span data-ttu-id="9b0ab-143">Instructions XLANG-s</span><span class="sxs-lookup"><span data-stu-id="9b0ab-143">XLANG-s Statements</span></span>](../core/xlang-s-statements.md)  
  
-   [<span data-ttu-id="9b0ab-144">Opérateurs et Variables XLANG-s</span><span class="sxs-lookup"><span data-stu-id="9b0ab-144">XLANG-s Variables and Operators</span></span>](../core/xlang-s-variables-and-operators.md)  
  
-   [<span data-ttu-id="9b0ab-145">Expressions XLANG-s</span><span class="sxs-lookup"><span data-stu-id="9b0ab-145">XLANG-s Expressions</span></span>](../core/xlang-s-expressions.md)  
  
-   [<span data-ttu-id="9b0ab-146">Mots réservés XLANG-s</span><span class="sxs-lookup"><span data-stu-id="9b0ab-146">XLANG-s Reserved Words</span></span>](../core/xlang-s-reserved-words.md)  
  
-   [<span data-ttu-id="9b0ab-147">XLANG-s pour les Conversions de Type BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="9b0ab-147">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)  
  
## <a name="see-also"></a><span data-ttu-id="9b0ab-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b0ab-148">See Also</span></span>  
 [<span data-ttu-id="9b0ab-149">Sur le moteur d’Orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="9b0ab-149">About the BizTalk Orchestration Engine</span></span>](../core/about-the-biztalk-orchestration-engine.md)