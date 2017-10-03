---
title: "À l’aide de l’adressage IPv6 avec les adaptateurs BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93cd2ead-5e87-47ac-8f78-d56b80afd34e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e77defa2351bf8e180b63b8da5c6a8c4e0e5a4e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-ipv6-addressing-with-biztalk-adapters"></a><span data-ttu-id="5a90a-102">Utilisation de l'adressage IPv6 avec des adaptateurs BizTalk</span><span class="sxs-lookup"><span data-stu-id="5a90a-102">Using IPv6 Addressing with BizTalk Adapters</span></span>
<span data-ttu-id="5a90a-103">Les adaptateurs[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prennent en charge l'utilisation de l'adressage IPv6 lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur les systèmes d'exploitation [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a90a-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters support the use of IPv6 addressing when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on the [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] operating systems.</span></span> <span data-ttu-id="5a90a-104">Cette rubrique décrit la nomenclature de spécification d'une adresse IPv6 pour un chemin d'accès UNC, la nomenclature de spécification d'une adresse IPv6 littérale et l'utilisation des identificateurs d'étendue IPv6 avec les adaptateurs HTTP et SOAP.</span><span class="sxs-lookup"><span data-stu-id="5a90a-104">This topic describes the nomenclature that should be used to specify an IPv6 address for a UNC path, the nomenclature for specifying a literal IPv6 address, and the use of IPv6 scope identifiers with the HTTP and SOAP adapters.</span></span>  
  
## <a name="ipv6-address-nomenclature-used-for-a-unc-path"></a><span data-ttu-id="5a90a-105">Nomenclature d'adresse IPv6 utilisée pour un chemin d'accès UNC</span><span class="sxs-lookup"><span data-stu-id="5a90a-105">IPv6 Address Nomenclature Used for a UNC Path</span></span>  
 <span data-ttu-id="5a90a-106">Pour spécifier une adresse IPv6 littérale dans un chemin d'accès UNC, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5a90a-106">Follow these steps when specifying a literal IPv6 address in a UNC path:</span></span>  
  
1.  <span data-ttu-id="5a90a-107">Remplacer n’importe quel signe deux-points « : » par des tirets «- » caractères.</span><span class="sxs-lookup"><span data-stu-id="5a90a-107">Replace any colon ":" characters with a dash "-" character.</span></span>  
  
2.  <span data-ttu-id="5a90a-108">Ajoutez le texte «**IPv6 literal.net**» à l’adresse IP.</span><span class="sxs-lookup"><span data-stu-id="5a90a-108">Append the text "**.ipv6-literal.net**" to the IP address.</span></span>  
  
 <span data-ttu-id="5a90a-109">Par exemple, la nomenclature d'un URI pointant vers un partage de fichiers sur un ordinateur avec l'adresse IPv6 2001:DB8:2a:1005:230:48ff:fe73:989d serait comme suit :</span><span class="sxs-lookup"><span data-stu-id="5a90a-109">For example, the nomenclature for a URI that points to a file share on a computer with the IPv6 address 2001:DB8:2a:1005:230:48ff:fe73:989d would be:</span></span>  
  
```  
\\2001-DB8-2a-1005-230-48ff-fe73-989d.ipv6-literal.net\<sharename>  
```  
  
 <span data-ttu-id="5a90a-110">Où \< *nom_partage*> est le nom du partage de fichiers sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="5a90a-110">Where \<*sharename*> is the name of the file share on the target computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a90a-111">Assurez-vous que les comptes d'utilisateur pour les instances d'hôte dans lesquelles les gestionnaires d'envoi et de réception FILE sont exécutés disposent des autorisations appropriées sur le partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="5a90a-111">Ensure that the user accounts for the host instances that the File send and receive handlers are running in have appropriate permissions to the file share.</span></span> <span data-ttu-id="5a90a-112">Pour plus d’informations sur les autorisations de dossier requises pour recevoir des fichiers avec l’adaptateur File, consultez [comment configurer un gestionnaire de réception de fichier](http://msdn.microsoft.com/library/68333bb6-d79b-4a82-9742-230f62d535c4).</span><span class="sxs-lookup"><span data-stu-id="5a90a-112">For more information about the folder permissions required to receive files with the File adapter see [How to Configure a File Receive Handler](http://msdn.microsoft.com/library/68333bb6-d79b-4a82-9742-230f62d535c4).</span></span> <span data-ttu-id="5a90a-113">Pour plus d’informations sur les autorisations de dossier requises lors de l’envoi de fichiers avec l’adaptateur File, consultez [problèmes connus avec l’adaptateur File](../core/known-issues-with-the-file-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="5a90a-113">For more information about the folder permissions required when sending files with the File adapter see [Known Issues with the File Adapter](../core/known-issues-with-the-file-adapter.md).</span></span> <span data-ttu-id="5a90a-114">Pour plus d’informations sur les systèmes de fichiers qui sont pris en charge pour une utilisation avec l’adaptateur File, consultez [http://support.microsoft.com/kb/815070](http://support.microsoft.com/kb/815070).</span><span class="sxs-lookup"><span data-stu-id="5a90a-114">For information about the file systems that are supported for use with the File adapter, see [http://support.microsoft.com/kb/815070](http://support.microsoft.com/kb/815070).</span></span>  
  
## <a name="using-ipv6-scope-identifiers-with-the-http-adapter-and-the-soap-send-adapter"></a><span data-ttu-id="5a90a-115">Utilisation des identificateurs d'étendue IPv6 avec l'adaptateur HTTP et l'adaptateur d'envoi SOAP</span><span class="sxs-lookup"><span data-stu-id="5a90a-115">Using IPv6 Scope Identifiers with the HTTP Adapter and the SOAP Send Adapter</span></span>  
 <span data-ttu-id="5a90a-116">Adaptateur de réception et d’envoi HTTP et l’adaptateur d’envoi SOAP requièrent que si un identificateur de portée est utilisé dans une adresse IPv6, l’identificateur de portée doit être échappé avec le code d’échappement **% 25**.</span><span class="sxs-lookup"><span data-stu-id="5a90a-116">The HTTP send and receive adapter and the SOAP send adapter require that if a scope identifier is used in an IPv6 address, the scope identifier must be escaped with the escape code **%25**.</span></span> <span data-ttu-id="5a90a-117">Par exemple, **fe80::550c:489f:e65e:aef3 %8** est une adresse IPv6 valide contenant un identificateur de portée (%8).</span><span class="sxs-lookup"><span data-stu-id="5a90a-117">For example, **fe80::550c:489f:e65e:aef3%8** is a valid IPv6 address containing a scope identifier (%8).</span></span> <span data-ttu-id="5a90a-118">Pour utiliser cette adresse IPv6 avec les adaptateurs d'envoi et de réception HTTP ou l'adaptateur d'envoi SOAP, l'identificateur d'étendue doit être assorti d'un caractère d'échappement comme suit :</span><span class="sxs-lookup"><span data-stu-id="5a90a-118">To use this IPv6 address with the HTTP send and receive adapters or the SOAP send adapter, the scope identifier must be escaped as follows:</span></span>  
  
```  
fe80::550c:489f:e65e:aef3%258  
```  
  
## <a name="adapter-uri-nomenclature-used-for-a-literal-ipv6-address"></a><span data-ttu-id="5a90a-119">Nomenclature d'un URI d'adaptateur utilisée pour une adresse IPv6 littérale</span><span class="sxs-lookup"><span data-stu-id="5a90a-119">Adapter URI Nomenclature Used for a Literal IPv6 Address</span></span>  
  
-   <span data-ttu-id="5a90a-120">Pour utiliser une adresse IPv6 littérale pour un URI d'adaptateur, placez l'adresse IP entre crochets (« [ », « ] »).</span><span class="sxs-lookup"><span data-stu-id="5a90a-120">To use a literal IPv6 address for an adapter URI, enclose the IP address in square brackets "[", "]".</span></span> <span data-ttu-id="5a90a-121">Par exemple, la nomenclature d'un URI avec l'adresse IPv6 2001:DB8:2a:1005:230:48ff:fe73:989d serait comme suit :</span><span class="sxs-lookup"><span data-stu-id="5a90a-121">For example, the nomenclature for a URI with the IPv6 address 2001:DB8:2a:1005:230:48ff:fe73:989d would be:</span></span>  
  
    ```  
    [2001:DB8:2a:1005:230:48ff:fe73:989d]  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5a90a-122">L’utilisation du littéral d’une adresse IPv6 pour l’URI d’adaptateur suit les règles établies dans [RFC2732](http://go.microsoft.com/fwlink/?LinkId=90375).</span><span class="sxs-lookup"><span data-stu-id="5a90a-122">The use of literal IPv6 addresses for adapter URIs follows the guidelines established in [RFC2732](http://go.microsoft.com/fwlink/?LinkId=90375).</span></span>  
  
-   <span data-ttu-id="5a90a-123">Lorsqu'une adresse IPv6 littérale est spécifiée comme nom du serveur pour l'adaptateur de réception POP3, l'adaptateur d'envoi SMTP ou les adaptateurs d'envoi et de réception SQL, l'adresse IPv6 ne doit pas être placée entre crochets.</span><span class="sxs-lookup"><span data-stu-id="5a90a-123">When specifying a literal IPv6 address as the server name for the POP3 receive adapter, the SMTP send adapter, or the SQL send and receive adapters, the IPv6 address should not be enclosed in square brackets.</span></span>  
  
## <a name="summary-of-considerations-when-using-literal-ipv6-addressing-with-biztalk-adapters"></a><span data-ttu-id="5a90a-124">Résumé des considérations relatives à l'utilisation de l'adressage IPv6 littéral avec les adaptateurs BizTalk</span><span class="sxs-lookup"><span data-stu-id="5a90a-124">Summary of Considerations When Using Literal IPv6 Addressing with BizTalk Adapters</span></span>  
 <span data-ttu-id="5a90a-125">Le tableau suivant indique quand l'utilisation d'une adresse IPv6 littérale nécessite que l'adresse IP soit placée entre crochets (« [ », « ] ») et quand un identificateur d'étendue utilisé dans une adresse IPv6 doit être assorti d'un caractère d'échappement :</span><span class="sxs-lookup"><span data-stu-id="5a90a-125">The table below summarizes when the use of a literal IPv6 address requires that the IP address is enclosed in square brackets "[", "]" and when a scope identifier that is used in an IPv6 address must be escaped:</span></span>  
  
|<span data-ttu-id="5a90a-126">Adaptateur</span><span class="sxs-lookup"><span data-stu-id="5a90a-126">Adapter</span></span>|<span data-ttu-id="5a90a-127">Nécessite que l'adresse IPv6 littérale soit placée entre crochets ?</span><span class="sxs-lookup"><span data-stu-id="5a90a-127">Requires that literal IPv6 address is enclosed in square brackets?</span></span>|<span data-ttu-id="5a90a-128">Nécessite que l'identificateur d'étendue soit assorti d'un caractère d'échappement ?</span><span class="sxs-lookup"><span data-stu-id="5a90a-128">Requires that scope identifier is escaped?</span></span>|  
|-------------|------------------------------------------------------------------------|------------------------------------------------|  
|<span data-ttu-id="5a90a-129">Réception POP3</span><span class="sxs-lookup"><span data-stu-id="5a90a-129">POP3 receive</span></span>|<span data-ttu-id="5a90a-130">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-130">No</span></span>|<span data-ttu-id="5a90a-131">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-131">No</span></span>|  
|<span data-ttu-id="5a90a-132">Envoi SMTP</span><span class="sxs-lookup"><span data-stu-id="5a90a-132">SMTP send</span></span>|<span data-ttu-id="5a90a-133">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-133">No</span></span>|<span data-ttu-id="5a90a-134">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-134">No</span></span>|  
|<span data-ttu-id="5a90a-135">Envoi et réception SQL</span><span class="sxs-lookup"><span data-stu-id="5a90a-135">SQL send and receive</span></span>|<span data-ttu-id="5a90a-136">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-136">No</span></span>|<span data-ttu-id="5a90a-137">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-137">No</span></span>|  
|<span data-ttu-id="5a90a-138">Envoi et réception FILE</span><span class="sxs-lookup"><span data-stu-id="5a90a-138">File send and receive</span></span>|<span data-ttu-id="5a90a-139">Non (voir la section **Nomenclature d’adresse IPv6 utilisée pour un chemin d’accès UNC**)</span><span class="sxs-lookup"><span data-stu-id="5a90a-139">No (see section **IPv6 Address Nomenclature Used for a UNC Path**)</span></span>|<span data-ttu-id="5a90a-140">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-140">No</span></span>|  
|<span data-ttu-id="5a90a-141">Envoi et réception HTTP</span><span class="sxs-lookup"><span data-stu-id="5a90a-141">HTTP send and receive</span></span>|<span data-ttu-id="5a90a-142">Oui</span><span class="sxs-lookup"><span data-stu-id="5a90a-142">Yes</span></span>|<span data-ttu-id="5a90a-143">Oui</span><span class="sxs-lookup"><span data-stu-id="5a90a-143">Yes</span></span>|  
|<span data-ttu-id="5a90a-144">Envoi et réception MQSeries</span><span class="sxs-lookup"><span data-stu-id="5a90a-144">MQSeries send and receive</span></span>|<span data-ttu-id="5a90a-145">Oui</span><span class="sxs-lookup"><span data-stu-id="5a90a-145">Yes</span></span>|<span data-ttu-id="5a90a-146">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-146">No</span></span>|  
|<span data-ttu-id="5a90a-147">Envoi et réception MSMQ</span><span class="sxs-lookup"><span data-stu-id="5a90a-147">MSMQ send and receive</span></span>|<span data-ttu-id="5a90a-148">Oui</span><span class="sxs-lookup"><span data-stu-id="5a90a-148">Yes</span></span>|<span data-ttu-id="5a90a-149">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-149">No</span></span>|  
|<span data-ttu-id="5a90a-150">Envoi SOAP</span><span class="sxs-lookup"><span data-stu-id="5a90a-150">SOAP send</span></span>|<span data-ttu-id="5a90a-151">Oui</span><span class="sxs-lookup"><span data-stu-id="5a90a-151">Yes</span></span>|<span data-ttu-id="5a90a-152">Oui</span><span class="sxs-lookup"><span data-stu-id="5a90a-152">Yes</span></span>|  
|<span data-ttu-id="5a90a-153">Réception SOAP</span><span class="sxs-lookup"><span data-stu-id="5a90a-153">SOAP receive</span></span>|<span data-ttu-id="5a90a-154">Oui</span><span class="sxs-lookup"><span data-stu-id="5a90a-154">Yes</span></span>|<span data-ttu-id="5a90a-155">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-155">No</span></span>|  
|<span data-ttu-id="5a90a-156">Envoi et réception WCF</span><span class="sxs-lookup"><span data-stu-id="5a90a-156">WCF send and receive</span></span>|<span data-ttu-id="5a90a-157">Oui</span><span class="sxs-lookup"><span data-stu-id="5a90a-157">Yes</span></span>|<span data-ttu-id="5a90a-158">Non</span><span class="sxs-lookup"><span data-stu-id="5a90a-158">No</span></span>|