---
title: "À l’aide de l’authentification unique efficacement dans le Service de la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, service solutions
- service solution tutorial, SSO
- SSO, using from code
ms.assetid: 809e0ad3-cc7f-4095-87d1-63031675a47f
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66dafba56bdeedb8c7b35b4442623f55e70f1305
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-sso-efficiently-in-the-service-oriented-solution"></a><span data-ttu-id="63c45-102">À l’aide de l’authentification unique efficacement dans le Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="63c45-102">Using SSO Efficiently in the Service Oriented Solution</span></span>
<span data-ttu-id="63c45-103">La solution orientée services utilise l'authentification unique de l'entreprise (SSO) pour stocker les valeurs de configuration et pour gérer les informations d'identification pour les systèmes principaux.</span><span class="sxs-lookup"><span data-stu-id="63c45-103">The service oriented solution uses Enterprise Single Sign-On (SSO) both to store configuration values and to handle credentials for the back-end systems.</span></span> <span data-ttu-id="63c45-104">Pour réduire la latence, la solution utilise un cache local pour les valeurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="63c45-104">To reduce latency, the solution uses a local cache for the configuration values.</span></span> <span data-ttu-id="63c45-105">La solution actualise le cache toutes les cinq minutes.</span><span class="sxs-lookup"><span data-stu-id="63c45-105">The solution refreshes the cache every five minutes.</span></span>  
  
 <span data-ttu-id="63c45-106">Dans de nombreuses applications, les adaptateurs gèrent les applications SSO, notamment en obtenant un ticket SSO, en échangeant le ticket et en utilisant les informations d'identification pour accéder à l'application associée.</span><span class="sxs-lookup"><span data-stu-id="63c45-106">In many applications, the adapters handle the SSO operations—including getting an SSO ticket, redeeming the ticket, and using the credentials to gain access to the affiliate application.</span></span> <span data-ttu-id="63c45-107">Toutefois, la version Inline de la solution orientée services n'utilise pas d'adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="63c45-107">However, the inline version of the service oriented solution does not use adapters.</span></span> <span data-ttu-id="63c45-108">Elle doit utiliser l'authentification unique à partir du code.</span><span class="sxs-lookup"><span data-stu-id="63c45-108">It must use SSO from code.</span></span>  
  
 <span data-ttu-id="63c45-109">Cette rubrique décrit le mécanisme de mise en cache utilisé par la solution ainsi que l'utilisation de l'authentification unique à partir du code par la version Inline de la solution.</span><span class="sxs-lookup"><span data-stu-id="63c45-109">This topic describes the caching mechanism used by the solution, as well as how the inline version of the solution uses SSO from code.</span></span>  
  
## <a name="local-caching-of-configuration-values"></a><span data-ttu-id="63c45-110">Mise en cache local des valeurs de configuration</span><span class="sxs-lookup"><span data-stu-id="63c45-110">Local Caching of Configuration Values</span></span>  
 <span data-ttu-id="63c45-111">La solution orientée services utilise deux objets, **ConfigPropertyBag** et **ConfigParameters**, pour gérer les valeurs de configuration.</span><span class="sxs-lookup"><span data-stu-id="63c45-111">The service oriented solution uses two objects, **ConfigPropertyBag** and **ConfigParameters**, to handle the configuration values.</span></span> <span data-ttu-id="63c45-112">Le **ConfigPropertyBag** contient les valeurs de classe et est utilisée uniquement par le **ConfigParameters** classe.</span><span class="sxs-lookup"><span data-stu-id="63c45-112">The **ConfigPropertyBag** class holds the values and is used only by the **ConfigParameters** class.</span></span> <span data-ttu-id="63c45-113">Le **ConfigParameters** classe est utilisée par les autres parties de la solution pour récupérer les paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="63c45-113">The **ConfigParameters** class is used by the other parts of the solution to retrieve the configuration parameters.</span></span> <span data-ttu-id="63c45-114">Les deux classes se trouvent dans le **Microsoft.Samples.BizTalk.WoodgroveBank.ConfigHelper** espace de noms.</span><span class="sxs-lookup"><span data-stu-id="63c45-114">Both classes are in the **Microsoft.Samples.BizTalk.WoodgroveBank.ConfigHelper** namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63c45-115">La solution orientée services définit l'intervalle d'actualisation du cache sur 300 secondes (5  minutes).</span><span class="sxs-lookup"><span data-stu-id="63c45-115">The Service Oriented solution fixes the cache refresh interval at 300 seconds (5 minutes).</span></span> <span data-ttu-id="63c45-116">Vous pouvez aussi faire de l'intervalle d'actualisation du cache une propriété configurable dans cette solution.</span><span class="sxs-lookup"><span data-stu-id="63c45-116">You may, instead, want to make the cache refresh interval itself  a configurable property in this solution.</span></span> <span data-ttu-id="63c45-117">Cela est effectué dans la solution de gestion des processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="63c45-117">This is done in the Business Process Management solution.</span></span> <span data-ttu-id="63c45-118">Pour plus d’informations sur la façon dont cette solution gère l’authentification unique, consultez [à l’aide de l’authentification unique efficacement dans la Solution de gestion des processus métier](../core/using-sso-efficiently-in-the-business-process-management-solution.md).</span><span class="sxs-lookup"><span data-stu-id="63c45-118">For more information about how that solution handles SSO, see [Using SSO Efficiently in the Business Process Management Solution](../core/using-sso-efficiently-in-the-business-process-management-solution.md).</span></span> <span data-ttu-id="63c45-119">Notez que, dans un tel cas, une modification de l'intervalle d'actualisation ne prend effet qu'au moment où le cache est actualisé à la fin de l'ancien intervalle.</span><span class="sxs-lookup"><span data-stu-id="63c45-119">Notice that, in such a case, a change in the refresh interval does not take effect until the cache is refreshed at the end of the old interval time.</span></span>  
  
 <span data-ttu-id="63c45-120">Le **ConfigPropertyBag** présente les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="63c45-120">The **ConfigPropertyBag** has the following methods:</span></span>  
  
|<span data-ttu-id="63c45-121">Méthode</span><span class="sxs-lookup"><span data-stu-id="63c45-121">Method</span></span>|<span data-ttu-id="63c45-122"> Description</span><span class="sxs-lookup"><span data-stu-id="63c45-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="63c45-123">Lecture</span><span class="sxs-lookup"><span data-stu-id="63c45-123">Read</span></span>|<span data-ttu-id="63c45-124">Extrait une valeur pour une propriété donnée.</span><span class="sxs-lookup"><span data-stu-id="63c45-124">Retrieves a value for a given property.</span></span>|  
|<span data-ttu-id="63c45-125">Write</span><span class="sxs-lookup"><span data-stu-id="63c45-125">Write</span></span>|<span data-ttu-id="63c45-126">Attribue une valeur à une propriété.</span><span class="sxs-lookup"><span data-stu-id="63c45-126">Assigns a value to a property.</span></span>|  
  
 <span data-ttu-id="63c45-127">La classe utilise une instance de .NET **NameValueCollection** pour contenir les valeurs.</span><span class="sxs-lookup"><span data-stu-id="63c45-127">The class uses an instance of a .NET **NameValueCollection** to hold the values.</span></span> <span data-ttu-id="63c45-128">Les deux méthodes d’accès implémentent la **IPropertyBag** de l’interface à partir de la **Microsoft.BizTalk.SSOClient.Interop** espace de noms.</span><span class="sxs-lookup"><span data-stu-id="63c45-128">The two access methods implement the **IPropertyBag** interface from the **Microsoft.BizTalk.SSOClient.Interop** namespace.</span></span> <span data-ttu-id="63c45-129">Le **ConfigPropertyBag** classe est une classe interne et utilisée uniquement par le **ConfigParameters** classe.</span><span class="sxs-lookup"><span data-stu-id="63c45-129">The **ConfigPropertyBag** class is an internal class and used only by the **ConfigParameters** class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63c45-130">Les noms de clé dans le jeu de propriétés ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="63c45-130">Key names in the property bag are case insensitive.</span></span> <span data-ttu-id="63c45-131">Sous-jacent **NameValueCollection** utilise un hachage pas la casse et les comparaisons sans respecter la casse.</span><span class="sxs-lookup"><span data-stu-id="63c45-131">The underlying **NameValueCollection** uses case-insensitive hashing and case-insensitive comparisons.</span></span>  
  
 <span data-ttu-id="63c45-132">L’application utilise le **ConfigParameters** classe pour gérer les valeurs de configuration de l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="63c45-132">The application uses the **ConfigParameters** class to handle the SSO configuration values.</span></span> <span data-ttu-id="63c45-133">La classe possède les méthodes publiques et attributs suivants :</span><span class="sxs-lookup"><span data-stu-id="63c45-133">The class has the following public methods and attributes:</span></span>  
  
|<span data-ttu-id="63c45-134">Méthode ou attribut</span><span class="sxs-lookup"><span data-stu-id="63c45-134">Method or Attribute</span></span>|<span data-ttu-id="63c45-135"> Description</span><span class="sxs-lookup"><span data-stu-id="63c45-135">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="63c45-136">SSOConfigParameter</span><span class="sxs-lookup"><span data-stu-id="63c45-136">SSOConfigParameter</span></span>|<span data-ttu-id="63c45-137">Énumération pour spécifier les paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="63c45-137">An enumeration for specifying configuration parameters.</span></span>|  
|<span data-ttu-id="63c45-138">GetConfigParameters</span><span class="sxs-lookup"><span data-stu-id="63c45-138">GetConfigParameters</span></span>|<span data-ttu-id="63c45-139">Méthode utilisée pour récupérer une valeur pour un paramètre donné.</span><span class="sxs-lookup"><span data-stu-id="63c45-139">A method used to retrieve a value for a given parameter.</span></span> <span data-ttu-id="63c45-140">Utilise SSOConfigParameter pour indiquer le paramètre.</span><span class="sxs-lookup"><span data-stu-id="63c45-140">Uses the SSOConfigParameter to indicate the parameter.</span></span>|  
  
 <span data-ttu-id="63c45-141">Le **ConfigParameters** classe utilise la classe .NET Timer et une fonction déléguée pour configurer l’actualisation de la **ConfigPropertyBag**:</span><span class="sxs-lookup"><span data-stu-id="63c45-141">The **ConfigParameters** class uses the .NET Timer class and a delegate function to set up the refresh of the **ConfigPropertyBag**:</span></span>  
  
```  
private static Timer cacheRefreshTimer;  
private static ISSOConfigStore ssoConfigStore;  
private static ReaderWriterLock syncLock;  
  
// Cache refresh interval in milliseconds  
private const int CacheRefreshInterval = 5 * 60 * 1000;  
private static ConfigPropertyBag ssoPropBag;  
  
static ConfigParameters()  
{  
    ssoConfigStore = new ISSOConfigStore();  
    ssoPropBag = new ConfigPropertyBag();  
    syncLock = new ReaderWriterLock();  
  
    ssoConfigStore.GetConfigInfo(SSO_CONFIG_APP,  
         SSO_IDENTIFIER_NAME, SSOFlag.SSO_FLAG_RUNTIME,  
         ssoPropBag);  
  
    cacheRefreshTimer = new Timer(  
        new TimerCallback(ConfigParameters.cacheRefreshCallback),  
        null, CacheRefreshInterval, CacheRefreshInterval);  
}  
```  
  
 <span data-ttu-id="63c45-142">Notez que le constructeur statique initialise les variables de membres statiques, permettant ainsi l'utilisation de méthodes de classe sans créer d'instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="63c45-142">Notice that the static constructor initializes the static member variables thus enabling the use of class methods without creating an instance of the class.</span></span> <span data-ttu-id="63c45-143">Le constructeur crée des instances de la banque de configuration de l’authentification unique (**ISSOConfigStore**), le jeu de propriétés de configuration (**ConfigPropertyBag**) et le verrouillage de synchronisation ( **ReaderWriterLock**) permet de contrôler l’accès à la **ConfigurationPropertyBag** pendant les mises à jour et des lectures.</span><span class="sxs-lookup"><span data-stu-id="63c45-143">The constructor creates instances of the SSO configuration store (**ISSOConfigStore**), the configuration property bag (**ConfigPropertyBag**), and a synchronization lock (**ReaderWriterLock**) used to control access to the **ConfigurationPropertyBag** during updates and reads.</span></span> <span data-ttu-id="63c45-144">Le constructeur utilise ensuite **GetConfigInfo** pour récupérer les valeurs de configuration de l’authentification unique et les placer dans le jeu de propriétés.</span><span class="sxs-lookup"><span data-stu-id="63c45-144">The constructor then uses **GetConfigInfo** to retrieve the SSO configuration values and to put them in the property bag.</span></span> <span data-ttu-id="63c45-145">Enfin, le constructeur crée un **Timer** objet qui, après l’intervalle spécifié, appelle la fonction déléguée, **cacheRefreshCallback**.</span><span class="sxs-lookup"><span data-stu-id="63c45-145">Finally, the constructor creates a **Timer** object that, after the specified interval, calls the delegate function, **cacheRefreshCallback**.</span></span>  
  
 <span data-ttu-id="63c45-146">Le **Timer** fonction déléguée est relativement simple :</span><span class="sxs-lookup"><span data-stu-id="63c45-146">The **Timer** delegate function is relatively straightforward:</span></span>  
  
```  
private static void cacheRefreshCallback(object state)  
{  
    // Disable the timer until we are done loading the cache.  
    cacheRefreshTimer.Change(Timeout.Infinite, CacheRefreshInterval);  
  
    // Put the data from SSO in a new property bag so that  
    // we don't have to lock the property bag and block it from being  
    // used. The SSO call is a remote call and may take a while.  
    ConfigPropertyBag propBag2 = new ConfigPropertyBag();  
    ssoConfigStore.GetConfigInfo(SSO_CONFIG_APP,   
        SSO_IDENTIFIER_NAME, SSOFlag.SSO_FLAG_RUNTIME, propBag2);  
  
    // Get a writer lock before updating the cached values.  
    syncLock.AcquireWriterLock(Timeout.Infinite);  
  
    try  
    {  
        ssoPropBag = propBag2;  
    }  
    finally   
    {  
        syncLock.ReleaseWriterLock();  
    }  
    // Enable the timer.  
    cacheRefreshTimer.Change(CacheRefreshInterval,   
        CacheRefreshInterval);  
}  
```  
  
 <span data-ttu-id="63c45-147">Notez que la méthode de rappel d'actualisation du cache désactive le minuteur afin que la méthode puisse s'exécuter complètement.</span><span class="sxs-lookup"><span data-stu-id="63c45-147">Notice that the cache refresh callback method disables the timer so that the method can run all the way through.</span></span> <span data-ttu-id="63c45-148">Remarquez également l'utilisation des verrous pour contrôler l'accès au jeu de propriétés.</span><span class="sxs-lookup"><span data-stu-id="63c45-148">Also notice the use of the locks to control access to the property bag.</span></span> <span data-ttu-id="63c45-149">Le **ReaderWriterLock** constitue le meilleur choix ici, il est conçu pour les cas où il y a plus de lectures que d’écritures.</span><span class="sxs-lookup"><span data-stu-id="63c45-149">The **ReaderWriterLock** is the best choice here—it is designed for cases where there are more reads than writes.</span></span> <span data-ttu-id="63c45-150">Notez également que le verrou, **syncLock**, est statique et déclarée au niveau de la classe de niveau que tous les threads partagent la même instance de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="63c45-150">Notice also that the lock, **syncLock**, is static and declared at the class level that all threads share the same, single instance of it.</span></span>  
  
## <a name="using-sso-from-code"></a><span data-ttu-id="63c45-151">Utilisation de l'authentification unique à partir du code</span><span class="sxs-lookup"><span data-stu-id="63c45-151">Using SSO from Code</span></span>  
 <span data-ttu-id="63c45-152">Lorsque vous utilisez l’authentification unique à partir de code, le code doit jouer le rôle de la carte : autrement dit, récupérer le ticket d’authentification unique à partir du message, échanger le ticket pour obtenir le nom d’utilisateur et un mot de passe pour le système principal et, enfin, utilisez le système principal.</span><span class="sxs-lookup"><span data-stu-id="63c45-152">When using single sign-on from code, the code must take on the role of the adapter: that is,retrieve the SSO ticket from the message, redeem the ticket to get the user name and password for the back-end system, and, finally, use the back-end system.</span></span> <span data-ttu-id="63c45-153">La solution orientée services procède par l’intermédiaire du **GetPendingTransactionsResponse** méthode de la **PendingTransactionsCaller** objet.</span><span class="sxs-lookup"><span data-stu-id="63c45-153">The service-oriented solution does this through the **GetPendingTransactionsResponse** method of the **PendingTransactionsCaller** object.</span></span>  
  
 <span data-ttu-id="63c45-154">La méthode apparaît comme suit :</span><span class="sxs-lookup"><span data-stu-id="63c45-154">The method appears as follows:</span></span>  
  
```  
public static PendingTransactionsResponse GetPendingTransactionsResponse(XLANGMessage requestMsg)  
{  
    try  
    {  
        // Get config parameter values.  
        int ptTimeout = Convert.ToInt32(  
            ConfigParameters.GetConfigParameter(  
                ConfigParameters.  
                    SSOConfigParameter.  
                        PENDING_TRANSACTIONS_INLINE_TIMEOUT  
            )  
        );  
  
        string ptURL = ConfigParameters.GetConfigParameter(  
            ConfigParameters.  
                SSOConfigParameter.  
                    PENDING_TRANSACTIONS_URL  
        );  
        string ssoAffliateApp = ConfigParameters.  
            GetConfigParameter(ConfigParameters.  
                SSOConfigParameter.  
                    PENDING_TRANSACTIONS_SSO_AFFILIATE_APP  
            );  
  
        // Redeem the SSO ticket and get the userid/password to   
        // use to interact with Pending Transaction System.  
  
        // Extract the ticket…  
        string msgTicket = (string)requestMsg.  
            GetPropertyValue(typeof(BTS.SSOTicket));  
  
        // and the user name of the originating user.  
        string originatorSID = (string)requestMsg.  
            GetPropertyValue(  
                typeof(  
                    Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID  
                )  
            );  
  
        string pendTransUserName;  
        // Now, redeem the ticket.  
        string[] pendTransCredential =   
            ssoTicket.RedeemTicket(  
                ssoAffliateApp,  
                originatorSID,  
                msgTicket,  
                SSOFlag.SSO_FLAG_NONE,  
                out pendTransUserName  
            );   
  
        PendingTransactionsRequest req =   
            (PendingTransactionsRequest)requestMsg[0].  
                RetrieveAs(  
                    typeof(PendingTransactionsRequest)  
                );  
        PendingTransactionsResponse resp;  
  
        using (PendingTransactionsWebService  
            svc = new PendingTransactionsWebService())  
        {  
            svc.Url = ptURL;  
            svc.Timeout = ptTimeout;  
  
            // The web service uses basic authentication, so we  
            //need to send the user id and password in the request.  
            CredentialCache credCache = new CredentialCache();  
            NetworkCredential credentialToUse =  
                new NetworkCredential(  
                    pendTransUserName, pendTransCredential[0]  
                );  
            credCache.Add(new Uri(svc.Url), "Basic", credentialToUse);  
            svc.Credentials = credCache;  
  
            resp = svc.GetPendingTransactions(req);  
        }  
        return resp;                  
    }  
    catch (System.Net.WebException webEx)  
    {  
        if (webEx.Status == WebExceptionStatus.Timeout)  
        {  
            throw new PendingTransactionsTimeoutException();  
        }  
        else  
        {  
            Trace.WriteLine("Other Net.WebException: "  
                + webEx.ToString()   
                + (null == webEx.InnerException ? "" :  
                     ("Inner Exception: "   
                        + webEx.InnerException.ToString())  
                )  
            );  
            throw;  
        }  
    }  
    catch(System.Exception ex)  
    {  
        Trace.WriteLine("Other Exception: "  
            + ex.ToString()   
            + (null == ex.InnerException ? "" :   
                 ("Inner Exception: "  
                    + ex.InnerException.ToString())  
                  )  
            );  
        throw;  
    }  
}  
```  
  
 <span data-ttu-id="63c45-155">La méthode commence par récupérer les informations de configuration, notamment l'URL, pour le système principal et le nom de l'application principale (associée).</span><span class="sxs-lookup"><span data-stu-id="63c45-155">The method begins by retrieving configuration information, including the URL, for the back-end system and the name of the backend (affiliate) application.</span></span>  
  
 <span data-ttu-id="63c45-156">Pour échanger le ticket, la méthode doit extraire du message le ticket et le nom d'utilisateur à l'origine de la demande.</span><span class="sxs-lookup"><span data-stu-id="63c45-156">To redeem the ticket, the method must extract the ticket and original requesting user name from the message.</span></span> <span data-ttu-id="63c45-157">Le message contient le ticket comme l’une des propriétés de contexte de message, **BTS. SSOTicket**.</span><span class="sxs-lookup"><span data-stu-id="63c45-157">The message contains the ticket as one of the message context properties, **BTS.SSOTicket**.</span></span> <span data-ttu-id="63c45-158">Pour plus d’informations, consultez **propriétés de contexte de Message** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="63c45-158">For more information, see **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> <span data-ttu-id="63c45-159">La méthode extrait également le **OriginatorSID** à partir des propriétés de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="63c45-159">The method also extracts the **OriginatorSID** from the message context properties.</span></span> <span data-ttu-id="63c45-160">Avec le ticket et le nom de l'expéditeur, la méthode appelle la méthode RedeemTicket sur le ticket pour récupérer les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="63c45-160">With the ticket and the originator's name in hand, the method calls the RedeemTicket method on the ticket to retrieve the credentials.</span></span>  
  
 <span data-ttu-id="63c45-161">Le reste du code crée un cache .NET NetworkCredential pour les informations d'identification et appelle le service Web principal.</span><span class="sxs-lookup"><span data-stu-id="63c45-161">The remainder of the code creates a .NET NetworkCredential cache for the credentials and calls the back-end Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63c45-162">Comme le nom d'utilisateur et le mot de passe reviennent de l'authentification unique en texte clair, vous devez minimiser la durée de vie des variables contenant ces informations.</span><span class="sxs-lookup"><span data-stu-id="63c45-162">Because the user name and password come back from SSO in clear text, you want to minimize the lifetime of variables holding that information.</span></span> <span data-ttu-id="63c45-163">Notez que le code déclare les variables d’informations d’identification dans un **essayez** bloc.</span><span class="sxs-lookup"><span data-stu-id="63c45-163">Notice that the code declares the credential variables within a **try** block.</span></span> <span data-ttu-id="63c45-164">Ici, les variables expirent à la sortie à partir de la **essayez** bloc.</span><span class="sxs-lookup"><span data-stu-id="63c45-164">Here, the variables expire upon exit from the **try** block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c45-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63c45-165">See Also</span></span>  
 [<span data-ttu-id="63c45-166">Caractéristiques de l’implémentation du Service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="63c45-166">Implementation Highlights of the Service Oriented Solution</span></span>](../core/implementation-highlights-of-the-service-oriented-solution.md)