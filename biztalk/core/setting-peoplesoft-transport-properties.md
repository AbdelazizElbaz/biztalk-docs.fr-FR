---
title: "Définition des propriétés du Transport PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setting transport properties
- transport properties, setting
ms.assetid: 44b5f015-59f1-43a3-9673-a5ba40266843
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ecfd221d28312e84dcbaf7d8c83abc4f5191f54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-peoplesoft-transport-properties"></a><span data-ttu-id="a1680-102">Définition des propriétés du transport PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="a1680-102">Setting PeopleSoft Transport Properties</span></span>
<span data-ttu-id="a1680-103">Les propriétés de transport PeopleSoft sont utilisées au moment de la conception et de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a1680-103">The PeopleSoft transport properties are used for design and run time.</span></span> <span data-ttu-id="a1680-104">Dans le **propriétés du Transport** boîte de dialogue, vous définissez les paramètres de connexion et les informations d’identification spécifique sur le système du serveur et les objets que vous essayez d’accéder.</span><span class="sxs-lookup"><span data-stu-id="a1680-104">In the **Transport Properties** dialog box, you set the connection and credential parameters specific to the server system and the objects you are trying to access.</span></span>  
  
 ![](../core/media/peop-peoplesofttransportpropertiess.gif "Peop_PeopleSoftTransportPropertiess")  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="a1680-105">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="a1680-105">To create a send port</span></span>  
  
1.  <span data-ttu-id="a1680-106">Développez les propriétés obligatoires de l'adaptateur et indiquez toutes les informations requises pour la connexion au serveur PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="a1680-106">Expand the Adapter Required Properties and fill in all required information for connection to the PeopleSoft server.</span></span>  
  
     <span data-ttu-id="a1680-107">Vous devez définir les paramètres de configuration afin de connecter l'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise à PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="a1680-107">You must set configuration parameters to connect Microsoft BizTalk Adapter for PeopleSoft Enterprise to PeopleSoft Enterprise.</span></span> <span data-ttu-id="a1680-108">Ces données respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="a1680-108">This data is case sensitive.</span></span>  
  
    |<span data-ttu-id="a1680-109">Paramètre</span><span class="sxs-lookup"><span data-stu-id="a1680-109">Parameter</span></span>|<span data-ttu-id="a1680-110"> Description</span><span class="sxs-lookup"><span data-stu-id="a1680-110">Description</span></span>|  
    |---------------|-----------------|  
    |`Application Server Path`|<span data-ttu-id="a1680-111">Chaîne représentant l'ordinateur et le port sur lesquels le serveur d'applications PeopleSoft est exécuté et à l'écoute.</span><span class="sxs-lookup"><span data-stu-id="a1680-111">A string representing the computer and port on which the PeopleSoft Application Server is running and listening.</span></span> <span data-ttu-id="a1680-112">La syntaxe du chemin d’accès d’URL pour l’Application PeopleSoft 8 est / / < nom_ordinateur > :\<port >.</span><span class="sxs-lookup"><span data-stu-id="a1680-112">The syntax of the URL path to the PeopleSoft 8 Application is //<computer_name>:\<port>.</span></span> <span data-ttu-id="a1680-113">Demandez à votre administrateur PeopleSoft pour le \<port > valeur.</span><span class="sxs-lookup"><span data-stu-id="a1680-113">Ask your PeopleSoft administrator for the \<port> value.</span></span> <span data-ttu-id="a1680-114">Le \<port > valeur est le JOLT port d’écoute de protocole, pas le port du serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="a1680-114">The \<port> value is the JOLT protocol listener port, not the App Server port.</span></span> <span data-ttu-id="a1680-115">Le port JOLT par défaut est 9000.</span><span class="sxs-lookup"><span data-stu-id="a1680-115">The default JOLT port is 9000.</span></span>|  
    |`JAVA_HOME`|<span data-ttu-id="a1680-116">Définissez la variable JAVA_HOME pointe vers votre installation JDK, par exemple : **C:\j2sdk1.4.2_08**.</span><span class="sxs-lookup"><span data-stu-id="a1680-116">Set the JAVA_HOME variable to point to your JDK installation, for example: **C:\j2sdk1.4.2_08**.</span></span>|  
    |`Password`|<span data-ttu-id="a1680-117">Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour PeopleSoft Enterprise accéder au système de serveur.</span><span class="sxs-lookup"><span data-stu-id="a1680-117">If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for PeopleSoft Enterprise to access the server system.</span></span><br /><br /> <span data-ttu-id="a1680-118">Chaîne représentant le mot de passe de l'utilisateur pour la connexion à un système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="a1680-118">A string representing the user's password for logon to a PeopleSoft system.</span></span> <span data-ttu-id="a1680-119">Les caractères ne sont pas visibles, mais sont représentés par des astérisques (*).</span><span class="sxs-lookup"><span data-stu-id="a1680-119">The characters do not appear but are represented by asterisks (*).</span></span>|  
    |`PeopleSoft 8.x Jar Files`|<span data-ttu-id="a1680-120">Pour utiliser des interfaces Ccmponent (PeopleSoft 8 uniquement), vous devez mettre à jour le paramètre CLASSPATH de façon à inclure le fichier jar de l'interface de composant pour PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="a1680-120">To use Ccmponent interfaces (PeopleSoft 8 only) you must update your CLASSPATH to include the PeopleSoft Component Interface jar file.</span></span> <span data-ttu-id="a1680-121">Par exemple : **< PeopleSoft_Home > \web\PSJOA\psjoa.jar**.</span><span class="sxs-lookup"><span data-stu-id="a1680-121">For example: **<PeopleSoft_Home>\web\PSJOA\psjoa.jar**.</span></span>|  
    |`User Name`|<span data-ttu-id="a1680-122">Si vous n’avez pas sélectionné **utiliser SSO**, vous devez définir les paramètres d’informations d’identification pour l’adaptateur BizTalk pour PeopleSoft Enterprise accéder au système de serveur.</span><span class="sxs-lookup"><span data-stu-id="a1680-122">If you did not select **Use SSO**, you must set credential parameters for the BizTalk Adapter for PeopleSoft Enterprise to access the server system.</span></span><br /><br /> <span data-ttu-id="a1680-123">Chaîne représentant un nom d'utilisateur requis pour la connexion à un système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="a1680-123">A string representing a user name required for logon to a PeopleSoft system.</span></span>|  
  
2.  <span data-ttu-id="a1680-124">Entrez un **des paramètres supplémentaires** de valeur lorsqu’une date est utilisée en tant que clé ; il a un format différent.</span><span class="sxs-lookup"><span data-stu-id="a1680-124">Enter an **Additional parameters** value when a date is used as a key; it has a different format.</span></span> <span data-ttu-id="a1680-125">Le format par défaut est JJ-MM-AAAA.</span><span class="sxs-lookup"><span data-stu-id="a1680-125">YYYY-MM-DD is the default format.</span></span>  
  
3.  <span data-ttu-id="a1680-126">Entrez un **contrôle d’accès concurrentiel** valeur représentant le nombre d’appels, par exemple 200, dans **nombre maximal d’appels simultanés** si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a1680-126">Enter a **Concurrency control** value representing the number of calls, for example 200, in **Max Concurrent Calls** if it is required.</span></span>  
  
     <span data-ttu-id="a1680-127">Le **nombre maximal d’appels simultanés** paramètre active une protection contre la surcharge si le serveur principal ne peut pas traiter la quantité de données.</span><span class="sxs-lookup"><span data-stu-id="a1680-127">The **Max Concurrent Calls** parameter activates an overload protection if the back-end server cannot process the amount of data.</span></span> <span data-ttu-id="a1680-128">Un appel simultané est une requête pour laquelle l'adaptateur n'a pas encore de réponse.</span><span class="sxs-lookup"><span data-stu-id="a1680-128">A concurrent call is a request for which the adapter does not yet have a reply.</span></span> <span data-ttu-id="a1680-129">Définissez **nombre maximal d’appels simultanés** dans les cas où le débit dépasse les capacités de traitement principal.</span><span class="sxs-lookup"><span data-stu-id="a1680-129">Set **Max Concurrent Calls** in instances where the throughput exceeds back-end processing capabilities.</span></span>  
  
     <span data-ttu-id="a1680-130">La valeur par défaut de ce champ est -1, ce qui correspond à l'absence de protection.</span><span class="sxs-lookup"><span data-stu-id="a1680-130">The default value for this field is -1, meaning no protection occurs.</span></span>  
  
     <span data-ttu-id="a1680-131">Si BizTalk Server envoie une demande pour l’adaptateur de transmission et le nombre d’appelle égal à ou dépasse la valeur définie pour **nombre maximal d’appels simultanés**, le thread qui soumet la demande est enregistrée jusqu'à ce que le d’appels simultanés nombre descend en dessous de la valeur définie.</span><span class="sxs-lookup"><span data-stu-id="a1680-131">If BizTalk Server submits a request to the Transmit adapter, and the number of concurrent calls equals or exceeds the value set for **Max Concurrent Calls**, the thread submitting the request is saved until the concurrent calls number decreases to below the set value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1680-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1680-132">See Also</span></span>  
 [<span data-ttu-id="a1680-133">Création de gestionnaires d’envoi PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="a1680-133">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)