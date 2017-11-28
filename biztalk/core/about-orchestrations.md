---
title: "À propos des Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations
- Orchestration Designer
- orchestrations, about orchestrations
- Orchestration Designer, about Orchestration Designer
ms.assetid: c0d9a3fb-da87-42cc-9e9e-e2c37232e606
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd3c1abeeb2c42c399a54aea4ba0128cc19bcd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-orchestrations"></a><span data-ttu-id="19102-102">À propos des Orchestrations</span><span class="sxs-lookup"><span data-stu-id="19102-102">About Orchestrations</span></span>
<span data-ttu-id="19102-103">Une orchestration est un outil flexible et puissant servant à représenter un processus d'entreprise exécutable avec le langage XLANG/s.</span><span class="sxs-lookup"><span data-stu-id="19102-103">An orchestration is a flexible, powerful tool for representing an executable business process based on XLANG/s language.</span></span> <span data-ttu-id="19102-104">XLANG/s peut être considéré comme un langage de messagerie comportant certaines des fonctionnalités d'expression de C#.</span><span class="sxs-lookup"><span data-stu-id="19102-104">XLANG/s can be viewed as a messaging language with some of the expression capabilities of C#.</span></span> <span data-ttu-id="19102-105">Vous pouvez concevoir un flux, générer et interpréter des données, appeler un code personnalisé et organiser tout le processus dans un dessin visuel intuitif. Lors de l'exécution, le moteur d'orchestration BizTalk exécute les fichiers XLANG/s qui constituent les processus d'entreprise exécutables produits par le Concepteur d'orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="19102-105">You can design flow, interpret and generate data, call custom code, and organize the entire process in an intuitive visual drawing, and at run time, the BizTalk Orchestration Engine executes XLANG/s files which are the executable business processes that are produced by BizTalk Orchestration Designer.</span></span>  
  
 <span data-ttu-id="19102-106">Les messages, les actions d'envoi et de réception auxquels les messages sont soumis et les ports via lesquels ces derniers sont transportés sont tous des éléments fondamentaux des orchestrations.</span><span class="sxs-lookup"><span data-stu-id="19102-106">Messages, the send and receive actions that operate on them, and the ports through which they are transported are all fundamental elements of an orchestration.</span></span> <span data-ttu-id="19102-107">Le message est le moyen par lequel les orchestrations communiquent avec le monde extérieur ainsi que le support de transmission de l'e-business.</span><span class="sxs-lookup"><span data-stu-id="19102-107">The message is the medium by which orchestrations communicate with the outside world and by which e-business is conducted.</span></span>  
  
 <span data-ttu-id="19102-108">**Réception** et **envoyer** formes encapsulent les fonctionnalités que vous avez besoin pour recevoir des messages dans votre orchestration et envoyer des messages à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="19102-108">**Receive** and **Send** shapes encapsulate the functionality you need to receive messages into your orchestration and send messages from it.</span></span> <span data-ttu-id="19102-109">Nous vous recommandons de vous familiariser avec les diverses formes que le Concepteur d'orchestration fournit pour représenter le flux logique de votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="19102-109">You should become familiar with the various shapes that Orchestration Designer provides to represent the logical flow of your orchestration.</span></span>  
  
 <span data-ttu-id="19102-110">Vous devez comprendre les concepts d'orchestration avancés que sont par exemple les services Web, la corrélation et les transactions à long terme.</span><span class="sxs-lookup"><span data-stu-id="19102-110">You should understand advanced orchestration concepts such as Web services, correlation, and long-running transactions.</span></span> <span data-ttu-id="19102-111">Vous n'aurez peut-être pas besoin d'utiliser toutes ces fonctionnalités, mais il est judicieux que vous sachiez en quoi elles peuvent vous rendre service.</span><span class="sxs-lookup"><span data-stu-id="19102-111">You might not need to use all of these facilities, but it is helpful to know what they can do for you.</span></span>  
  
 <span data-ttu-id="19102-112">Les services Web sont des programmes comportant des interfaces qui adhèrent aux normes définies dans le langage WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="19102-112">Web services are programs with interfaces that adhere to the standards set forth in the Web Services Description Language (WSDL).</span></span> <span data-ttu-id="19102-113">En définissant des types de messages, des ports, des types de ports et des opérations de façon standard, des systèmes disparates peuvent communiquer efficacement entre eux.</span><span class="sxs-lookup"><span data-stu-id="19102-113">By defining message types, ports, port types, and operations in a standard way, disparate systems can communicate effectively with each other.</span></span>  
  
 <span data-ttu-id="19102-114">La corrélation est le mécanisme par lequel les messages sont associés à des instances d'exécution particulières d'une orchestration, de manière à ce que votre processus d'entreprise puisse récupérer les informations appropriées lors de l'exécution de plusieurs instances et du transfert de plusieurs messages.</span><span class="sxs-lookup"><span data-stu-id="19102-114">Correlation is the mechanism by which messages are associated with particular running instances of an orchestration, so that your business process gets the appropriate information when many instances are running and many messages are being sent back and forth.</span></span>  
  
 <span data-ttu-id="19102-115">Les transactions vous permettent de conserver correctement l'état d'une orchestration dans l'éventualité d'un problème inattendu.</span><span class="sxs-lookup"><span data-stu-id="19102-115">Transactions enable you to maintain the state of an orchestration appropriately if any unexpected issues arise.</span></span> <span data-ttu-id="19102-116">Le Concepteur d'orchestration offre divers moyens de gérer les exceptions, ce vous permet de faire face aux erreurs de façon contrôlée et prévisible.</span><span class="sxs-lookup"><span data-stu-id="19102-116">Orchestration Designer provides various ways to handle exceptions, which enable you to deal with errors in a controlled and predictable manner.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19102-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="19102-117">In This Section</span></span>  
  
-   [<span data-ttu-id="19102-118">L’aire de conception d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="19102-118">The Orchestration Design Surface</span></span>](../core/the-orchestration-design-surface.md)  
  
-   [<span data-ttu-id="19102-119">Onglet des Orchestrations BizTalk, boîte à outils</span><span class="sxs-lookup"><span data-stu-id="19102-119">BizTalk Orchestrations Tab, Toolbox</span></span>](../core/biztalk-orchestrations-tab-toolbox.md)  
  
-   [<span data-ttu-id="19102-120">Étapes de développement d’orchestrations</span><span class="sxs-lookup"><span data-stu-id="19102-120">Steps in Orchestration Development</span></span>](../core/steps-in-orchestration-development.md)  
  
-   [<span data-ttu-id="19102-121">Considérations de sécurité pour le développement d’Orchestrations</span><span class="sxs-lookup"><span data-stu-id="19102-121">Security Considerations for Developing Orchestrations</span></span>](../core/security-considerations-for-developing-orchestrations.md)  
  
-   [<span data-ttu-id="19102-122">Langage XLANG-s</span><span class="sxs-lookup"><span data-stu-id="19102-122">XLANG-s Language</span></span>](../core/xlang-s-language.md)  
  
-   [<span data-ttu-id="19102-123">Sur le moteur d’Orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="19102-123">About the BizTalk Orchestration Engine</span></span>](../core/about-the-biztalk-orchestration-engine.md)