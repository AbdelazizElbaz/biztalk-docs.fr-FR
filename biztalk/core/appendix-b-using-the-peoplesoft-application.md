---
title: "Annexe b : à l’aide de l’Application PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PeopleSoft, using
- using PeopleSoft application
ms.assetid: 36475836-1d23-4bb4-a3c1-cdd3fff28476
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ff5c7b2b15c709064174371f1fcab9beb95e42d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-b-using-the-peoplesoft-application"></a><span data-ttu-id="8061f-102">Annexe b : à l’aide de l’Application PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="8061f-102">Appendix B: Using the PeopleSoft Application</span></span>
<span data-ttu-id="8061f-103">Cette section décrit l'utilisation de différentes composantes de PeopleSoft qui peuvent être utiles pour tester votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="8061f-103">This section describes using different areas of PeopleSoft that could be useful in your orchestration testing.</span></span>  
  
 <span data-ttu-id="8061f-104">Lorsque vous utilisez PeopleSoft pour les ports de réception, vous devez utiliser PeopleTools pour créer un document XML.</span><span class="sxs-lookup"><span data-stu-id="8061f-104">When you use PeopleSoft for receive ports, you use PeopleTools to create an XML document.</span></span> <span data-ttu-id="8061f-105">L'interaction avec PeopleSoft ne requiert pas de configuration spéciale.</span><span class="sxs-lookup"><span data-stu-id="8061f-105">Nothing special is required to interact with PeopleSoft.</span></span> <span data-ttu-id="8061f-106">Pour un événement, vous devez être en mesure d’accéder à un **http\\\\:\<hôte > :\<port >** pour écouter les événements à partir de PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="8061f-106">For an event, you must be able to access to an **http\\\\:\<host>:\<port>** to listen for events from PeopleSoft.</span></span> <span data-ttu-id="8061f-107">Si un hôte et un port ne sont pas accessibles, vous pouvez définir un hôte et un port HTTP spécifiques en configurant PeopleSoft Integration Broker.</span><span class="sxs-lookup"><span data-stu-id="8061f-107">If a host and port is not available to you, you can set up a specific HTTP host and port by configuring the PeopleSoft Integration Broker.</span></span>  
  
 <span data-ttu-id="8061f-108">Pour terminer le test d’un PeopleSoft port de réception, [génération ou schéma XML dans PeopleSoft](../core/generating-xml-or-schema-in-peoplesoft.md) explique comment déclencher un événement PeopleSoft via la modification dans un environnement PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="8061f-108">To complete the testing of a PeopleSoft receive port, [Generating XML or Schema in PeopleSoft](../core/generating-xml-or-schema-in-peoplesoft.md) discusses how to trigger a PeopleSoft event by changing something in a PeopleSoft environment.</span></span> <span data-ttu-id="8061f-109">La modification active un fichier XML qui est envoyé au dossier que vous définissez dans l'orchestration pour être surveillé.</span><span class="sxs-lookup"><span data-stu-id="8061f-109">The change activates an XML file that is sent to the folder you set in the orchestration to be monitored.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8061f-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8061f-110">In This Section</span></span>  
  
-   [<span data-ttu-id="8061f-111">Génération XML ou schéma dans PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="8061f-111">Generating XML or Schema in PeopleSoft</span></span>](../core/generating-xml-or-schema-in-peoplesoft.md)  
  
-   [<span data-ttu-id="8061f-112">Création d’un Port et l’hôte de HTTP PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="8061f-112">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)