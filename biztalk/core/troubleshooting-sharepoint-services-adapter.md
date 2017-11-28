---
title: "Adaptateur de Services SharePoint de dépannage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77f88174-118d-4ed6-8449-c89ca195ce5c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f9885696df24cd5c5f8321ad3c6dd79d444559a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-sharepoint-services-adapter"></a><span data-ttu-id="400c7-102">Dépannage de l’adaptateur SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="400c7-102">Troubleshooting SharePoint Services Adapter</span></span>
<span data-ttu-id="400c7-103">Cette rubrique décrit le dépannage de l’adaptateur [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] (WSS).</span><span class="sxs-lookup"><span data-stu-id="400c7-103">This topic focuses on troubleshooting the [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] (WSS) adapter.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="400c7-104">Installation</span><span class="sxs-lookup"><span data-stu-id="400c7-104">Installation</span></span>  
 <span data-ttu-id="400c7-105">Lors de l’utilisation de l’adaptateur [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] (WSS), deux options s’offrent à vous :</span><span class="sxs-lookup"><span data-stu-id="400c7-105">When using the [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] (WSS) adapter, there are two options:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="400c7-106">**Utilisez le modèle objet Client** la valeur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="400c7-106">**Use Client OM** set to **Yes**.</span></span>|<span data-ttu-id="400c7-107">**Recommandé**.</span><span class="sxs-lookup"><span data-stu-id="400c7-107">**Recommended**.</span></span> <span data-ttu-id="400c7-108">Lorsque cette option est définie sur Oui, le modèle CSOM (Client-Side Object Model) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] est utilisé.</span><span class="sxs-lookup"><span data-stu-id="400c7-108">When set to Yes, the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM) is used.</span></span> <span data-ttu-id="400c7-109">L’adaptateur est installé lors de l’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="400c7-109">The adapter is installed when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed.</span></span> <span data-ttu-id="400c7-110">Aucune étape d’installation supplémentaire n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="400c7-110">There are no additional installation steps.</span></span> <span data-ttu-id="400c7-111">**Remarque :** le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation installe également automatiquement l’objet modèle composant redistribuable SharePoint disponible à l’adresse [http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482).</span><span class="sxs-lookup"><span data-stu-id="400c7-111">**Note:**  The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation also automatically installs the SharePoint Client Object Model Redistributable available at [http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482).</span></span>|  
|<span data-ttu-id="400c7-112">**Utilisez le modèle objet Client** la valeur **non**.</span><span class="sxs-lookup"><span data-stu-id="400c7-112">**Use Client OM** set to **No**.</span></span>|<span data-ttu-id="400c7-113">**Option déconseillée**.</span><span class="sxs-lookup"><span data-stu-id="400c7-113">**Deprecated**.</span></span> <span data-ttu-id="400c7-114">Utilise le modèle SSOM (Service-Side Object Model) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="400c7-114">Uses the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Service Side Object Model (SSOM).</span></span><br /><br /> <span data-ttu-id="400c7-115">Un service Web est installé sur l’ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], qui peut se trouver sur le même ordinateur que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou sur un ordinateur distinct.</span><span class="sxs-lookup"><span data-stu-id="400c7-115">A web service is installed on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer, which can be on the same computer as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or a separate computer.</span></span><br /><br /> <span data-ttu-id="400c7-116">Pour installer le service web, exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation sur le [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] ordinateur et recherchez **adaptateur Windows SharePoint Services**.</span><span class="sxs-lookup"><span data-stu-id="400c7-116">To install the web service, run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer and check **Windows SharePoint Services Adapter**.</span></span> <span data-ttu-id="400c7-117">Consultez [annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) pour les étapes d’installation spécifiques.</span><span class="sxs-lookup"><span data-stu-id="400c7-117">See [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) for specific installation steps.</span></span>|  
  
 <span data-ttu-id="400c7-118">**Utilisez le modèle objet Client** la valeur **Oui** est recommandé.</span><span class="sxs-lookup"><span data-stu-id="400c7-118">**Use Client OM** set to **Yes** is recommended.</span></span> <span data-ttu-id="400c7-119">Lorsque la valeur **Oui**, le service web n’est pas installé sur l’ordinateur SharePoint.</span><span class="sxs-lookup"><span data-stu-id="400c7-119">When set to **Yes**, the web service is NOT installed on the SharePoint computer.</span></span> <span data-ttu-id="400c7-120">Si vous préférez utiliser l’option de service web, vous devez définir **utiliser le modèle objet Client** à **non** sur la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="400c7-120">If you prefer to use the web service option, you must set **Use Client OM** to **No** on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="iis"></a><span data-ttu-id="400c7-121">IIS</span><span class="sxs-lookup"><span data-stu-id="400c7-121">IIS</span></span>  
 <span data-ttu-id="400c7-122">**Service web BTSharePointAdapterWS.asmx**</span><span class="sxs-lookup"><span data-stu-id="400c7-122">**BTSharePointAdapterWS.asmx web service**</span></span>  
  
 <span data-ttu-id="400c7-123">Lorsque l’adaptateur [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] est installé sur l’ordinateur SharePoint, le service Web BTSharePointAdapterWS.asmx est créé dans IIS sur l’ordinateur SharePoint.</span><span class="sxs-lookup"><span data-stu-id="400c7-123">When the [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] adapter is installed on the SharePoint computer, the BTSharePointAdapterWS.asmx web service is created in IIS on the SharePoint computer.</span></span> <span data-ttu-id="400c7-124">En général, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et SharePoint sont installés sur des ordinateurs distincts.</span><span class="sxs-lookup"><span data-stu-id="400c7-124">Typically, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SharePoint are installed on different computers.</span></span> <span data-ttu-id="400c7-125">Lorsque SharePoint est installé, la base de données SQL de contenu peut être placée en local sur l’ordinateur SharePoint, ou sur un serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] distant.</span><span class="sxs-lookup"><span data-stu-id="400c7-125">When SharePoint is installed, the content SQL database can be local to the SharePoint computer or on a remote [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="400c7-126">**Pool d’applications utilise le compte de domaine**</span><span class="sxs-lookup"><span data-stu-id="400c7-126">**Application Pool uses Domain account**</span></span>  
  
 <span data-ttu-id="400c7-127">Lorsque BizTalk et SharePoint sont installés sur des ordinateurs distincts, le pool d’applications IIS exécutant le service Web BTSharePointAdapterWS.asmx doit utiliser un compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="400c7-127">When BizTalk and SharePoint are on different computers, the IIS application pool running the BTSharePointAdapterWS.asmx web service must use a domain account.</span></span> <span data-ttu-id="400c7-128">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les bases de données BizTalk, [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] et les bases de données SharePoint [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont tous installés sur le même ordinateur, vous pouvez utiliser un compte local.</span><span class="sxs-lookup"><span data-stu-id="400c7-128">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the BizTalk databases, [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] and the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] SharePoint databases are all installed on the same computer, then a local account can be used.</span></span>  
  
 <span data-ttu-id="400c7-129">**Scénario double saut**</span><span class="sxs-lookup"><span data-stu-id="400c7-129">**Double-Hop Scenario**</span></span>  
  
 <span data-ttu-id="400c7-130">Lorsque trois ordinateurs sont impliqués ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]), ce scénario à double tronçon nécessite l’authentification Kerberos.</span><span class="sxs-lookup"><span data-stu-id="400c7-130">When there are three computers involved ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]), there is a double-hop scenario that requires Kerberos authentication.</span></span> <span data-ttu-id="400c7-131">L’adaptateur SharePoint sur l’ordinateur BizTalk effectue une requête POST vers le service Web BTSharePointAdapterWS.asmx sur l’ordinateur SharePoint.</span><span class="sxs-lookup"><span data-stu-id="400c7-131">The SharePoint adapter on the BizTalk computer does a POST request to the BTSharePointAdapterWS.asmx web service on the SharePoint computer.</span></span> <span data-ttu-id="400c7-132">L’ordinateur SharePoint interroge ensuite ses bases de données sur l’ordinateur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="400c7-132">The SharePoint computer then queries its databases on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
 <span data-ttu-id="400c7-133">Cette requête POST en provenance de l’adaptateur BizTalk doit aboutir.</span><span class="sxs-lookup"><span data-stu-id="400c7-133">This POST request from the BizTalk adapter must complete successfully.</span></span> <span data-ttu-id="400c7-134">Si vous suspectez une défaillance au niveau de l’authentification, consultez les journaux IIS.</span><span class="sxs-lookup"><span data-stu-id="400c7-134">If you suspect an authentication failure, review the IIS logs.</span></span> <span data-ttu-id="400c7-135">Par défaut, les journaux IIS sont dans c:\inetpub\logs\LogFiles\W3SVC*x*.</span><span class="sxs-lookup"><span data-stu-id="400c7-135">By default, the IIS logs are in c:\inetpub\logs\LogFiles\W3SVC*x*.</span></span> <span data-ttu-id="400c7-136">La requête POST doit afficher un code d’état 200 (réussite).</span><span class="sxs-lookup"><span data-stu-id="400c7-136">The POST request should display a 200 (success) status code.</span></span> <span data-ttu-id="400c7-137">Si un code d’état d’échec est retourné, comme une erreur 401.2, suivie d’une erreur 401.1, par un autre 4*xx* des erreurs, puis l’authentification en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="400c7-137">If a failed status code is returned, like a 401.2, followed by a 401.1, following by another 4*xx* error, then authentication may be failing.</span></span>  
  
 <span data-ttu-id="400c7-138">Lorsque vous utilisez l’authentification Kerberos, des noms de principal de service (SPN) sont requis et la délégation doit être activée.</span><span class="sxs-lookup"><span data-stu-id="400c7-138">When Kerberos authentication is used, service principal names (SPN) are required and delegation must be enabled.</span></span>  
  
## <a name="enable-kerberos-authentication"></a><span data-ttu-id="400c7-139">Activation de l’authentification Kerberos</span><span class="sxs-lookup"><span data-stu-id="400c7-139">Enable Kerberos Authentication</span></span>  
 <span data-ttu-id="400c7-140">Dans un scénario à double tronçon, l’authentification Kerberos et l’activation de la délégation sont requis.</span><span class="sxs-lookup"><span data-stu-id="400c7-140">In a double-hop scenario, Kerberos authentication and enabling delegation are required.</span></span> <span data-ttu-id="400c7-141">Les étapes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="400c7-141">Steps include:</span></span>  
  
1.  <span data-ttu-id="400c7-142">Activer **Negotiate** sur le serveur IIS/SharePoint.</span><span class="sxs-lookup"><span data-stu-id="400c7-142">Enable **Negotiate** on the IIS/SharePoint server.</span></span> <span data-ttu-id="400c7-143">[215383 : comment faire pour configurer IIS pour prendre en charge le protocole Kerberos et le protocole NTLM pour l’authentification réseau](http://support.microsoft.com/kb/215383) répertorie les étapes.</span><span class="sxs-lookup"><span data-stu-id="400c7-143">[215383: How to configure IIS to support both the Kerberos protocol and the NTLM protocol for network authentication](http://support.microsoft.com/kb/215383) lists the steps.</span></span>  
  
2.  <span data-ttu-id="400c7-144">Les noms de principal de service (SPN) sont requis pour les comptes de domaine exécutant le service [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et le pool d’applications sur l’ordinateur IIS/SharePoint.</span><span class="sxs-lookup"><span data-stu-id="400c7-144">Service Principal Names (SPNs) are required for the domain accounts executing the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Service and the Application Pool on the IIS/SharePoint computer.</span></span> <span data-ttu-id="400c7-145">Pour créer un nom de principal de service, utilisez l’outil de ligne de commande SetSPN.exe :</span><span class="sxs-lookup"><span data-stu-id="400c7-145">To create an SPN, use the SetSPN.exe command-line tool:</span></span>  
  
     [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]<span data-ttu-id="400c7-146">: [Une mise à jour pour Setspn.exe dans Windows Server 2003 est disponible](http://support.microsoft.com/kb/970536)</span><span class="sxs-lookup"><span data-stu-id="400c7-146">: [An update for Setspn.exe in Windows Server 2003 is available](http://support.microsoft.com/kb/970536)</span></span>  
  
     [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]<span data-ttu-id="400c7-147">8, [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] et [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]: [SetSPN](http://technet.microsoft.com/library/cc731241.aspx)</span><span class="sxs-lookup"><span data-stu-id="400c7-147"> 8, [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] and [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]: [SetSPN](http://technet.microsoft.com/library/cc731241.aspx)</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="400c7-148">La commande SetSPN nécessite des droits d’administrateur de domaine et peut être exécutée à partir de n’importe quel ordinateur dans le domaine.</span><span class="sxs-lookup"><span data-stu-id="400c7-148">SetSPN requires Domain Administrator rights and can be executed from any computer in the domain.</span></span>  
  
     <span data-ttu-id="400c7-149">Pour renvoyer une liste de tous les noms de principal de service enregistrés dans un compte de domaine :</span><span class="sxs-lookup"><span data-stu-id="400c7-149">To return a list of all SPNs registered to a domain account:</span></span>  
  
    ```  
    setspn.exe -l Domain\UserAccount  
    ```  
  
     <span data-ttu-id="400c7-150">Création des noms de principal de service :</span><span class="sxs-lookup"><span data-stu-id="400c7-150">Create the SPNs:</span></span>  
  
    1.  <span data-ttu-id="400c7-151">Créez un nom de principal de service pour le nom de domaine complet de l’ordinateur IIS/SharePoint :</span><span class="sxs-lookup"><span data-stu-id="400c7-151">Create an SPN for the FQDN of the IIS/SharePoint computer:</span></span>  
  
        ```  
        setspn.exe -s http/IISSharePointComputerName.domain.com domain\IISApplicationPoolDomainAccount  
        ```  
  
    2.  <span data-ttu-id="400c7-152">Créez un nom de principal de service pour le nom NETBIOS de l’ordinateur IIS/SharePoint :</span><span class="sxs-lookup"><span data-stu-id="400c7-152">Create an SPN for the NETBIOS name of the IIS/SharePoint computer:</span></span>  
  
        ```  
        setspn.exe -s http/IISSharePointComputerNamedomain\IISApplicationPoolDomainAccount  
        ```  
  
    3.  <span data-ttu-id="400c7-153">Créez un nom de principal de service pour le nom de domaine complet de l’ordinateur SQL Server utilisé par l’ordinateur IIS/SharePoint :</span><span class="sxs-lookup"><span data-stu-id="400c7-153">Create an SPN for the FQDN of the SQL Server computer used by the IIS/SharePoint computer:</span></span>  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerName.domain.com domain\SQLServerServiceDomainAccount  
        ```  
  
    4.  <span data-ttu-id="400c7-154">Créez un nom de principal de service pour le nom de domaine complet et le port TCP de l’ordinateur SQL Server utilisé par l’ordinateur IIS/SharePoint :</span><span class="sxs-lookup"><span data-stu-id="400c7-154">Create an SPN for the FQDN and TCP Port of the SQL Server computer used by the IIS/SharePoint computer:</span></span>  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerName.domain.com:1433 domain\SQLServerServiceDomainAccount  
        ```  
  
    5.  <span data-ttu-id="400c7-155">Créez un nom de principal de service pour le nom NETBIOS de l’ordinateur SQL Server utilisé par l’ordinateur IIS/SharePoint :</span><span class="sxs-lookup"><span data-stu-id="400c7-155">Create an SPN for the NETBIOS name of the SQL Server computer used by the IIS/SharePoint computer:</span></span>  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerNamedomain\SQLServerServiceDomainAccount  
        ```  
  
    6.  <span data-ttu-id="400c7-156">Créez un nom de principal de service pour le nom NETBIOS et le port TCP de l’ordinateur SQL Server utilisé par l’ordinateur IIS/SharePoint :</span><span class="sxs-lookup"><span data-stu-id="400c7-156">Create an SPN for the NETBIOS name:TCP Port of the SQL Server computer used by the IIS/SharePoint computer:</span></span>  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerName:1433 domain\SQLServerServiceDomainAccount  
        ```  
  
3.  <span data-ttu-id="400c7-157">Sur le contrôleur de domaine, accédez à **utilisateurs Active Directory & ordinateurs** et procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="400c7-157">On the Domain controller, go to **Active Directory Users & Computers** and do the following:</span></span>  
  
    1.  <span data-ttu-id="400c7-158">Vérifiez **n’approuver cet ordinateur pour la délégation à tous les services** pour les ordinateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="400c7-158">Check **Trust this computer for delegation to any service** for the following computers:</span></span>  
  
        -   <span data-ttu-id="400c7-159">Serveur SharePoint/IIS</span><span class="sxs-lookup"><span data-stu-id="400c7-159">SharePoint/IIS server</span></span>  
  
        -   <span data-ttu-id="400c7-160">Serveur SQL Server utilisé par SharePoint</span><span class="sxs-lookup"><span data-stu-id="400c7-160">SQL Server used by SharePoint</span></span>  
  
    2.  <span data-ttu-id="400c7-161">Vérifiez **compte est approuvé pour la délégation** et désactivez **compte est sensible et ne peut pas être délégué** pour les comptes de domaine suivants :</span><span class="sxs-lookup"><span data-stu-id="400c7-161">Check **Account is Trusted for Delegation** and uncheck **Account is sensitive and cannot be delegated** for the following domain accounts:</span></span>  
  
        -   <span data-ttu-id="400c7-162">Compte de domaine du service SQL Server</span><span class="sxs-lookup"><span data-stu-id="400c7-162">SQL Server service domain account</span></span>  
  
        -   <span data-ttu-id="400c7-163">Compte de domaine du pool d’applications IIS</span><span class="sxs-lookup"><span data-stu-id="400c7-163">IIS Application Pool domain account</span></span>  
  
 <span data-ttu-id="400c7-164">Pour la résolution des problèmes supplémentaires, accédez à [résolution des problèmes de l’adaptateur Windows SharePoint Services](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="400c7-164">For additional troubleshooting, go to [Troubleshooting the Windows SharePoint Services Adapter](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="400c7-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="400c7-165">See Also</span></span>  
 <span data-ttu-id="400c7-166">[Configurer SharePoint Services emplacement de réception](../core/configure-sharepoint-services-receive-location.md) </span><span class="sxs-lookup"><span data-stu-id="400c7-166">[Configure SharePoint Services Receive Location](../core/configure-sharepoint-services-receive-location.md) </span></span>  
 <span data-ttu-id="400c7-167">[Configurer le Port d’envoi SharePoint Services](../core/configure-sharepoint-services-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="400c7-167">[Configure SharePoint Services Send Port](../core/configure-sharepoint-services-send-port.md) </span></span>  
 [<span data-ttu-id="400c7-168">CSOM : L’adaptateur SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="400c7-168">CSOM: SharePoint Services Adapter</span></span>](../core/csom-sharepoint-services-adapter.md)