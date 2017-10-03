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
# <a name="using-sso-efficiently-in-the-service-oriented-solution"></a>À l’aide de l’authentification unique efficacement dans le Service de la Solution orientée services
La solution orientée services utilise l'authentification unique de l'entreprise (SSO) pour stocker les valeurs de configuration et pour gérer les informations d'identification pour les systèmes principaux. Pour réduire la latence, la solution utilise un cache local pour les valeurs de configuration. La solution actualise le cache toutes les cinq minutes.  
  
 Dans de nombreuses applications, les adaptateurs gèrent les applications SSO, notamment en obtenant un ticket SSO, en échangeant le ticket et en utilisant les informations d'identification pour accéder à l'application associée. Toutefois, la version Inline de la solution orientée services n'utilise pas d'adaptateurs. Elle doit utiliser l'authentification unique à partir du code.  
  
 Cette rubrique décrit le mécanisme de mise en cache utilisé par la solution ainsi que l'utilisation de l'authentification unique à partir du code par la version Inline de la solution.  
  
## <a name="local-caching-of-configuration-values"></a>Mise en cache local des valeurs de configuration  
 La solution orientée services utilise deux objets, **ConfigPropertyBag** et **ConfigParameters**, pour gérer les valeurs de configuration. Le **ConfigPropertyBag** contient les valeurs de classe et est utilisée uniquement par le **ConfigParameters** classe. Le **ConfigParameters** classe est utilisée par les autres parties de la solution pour récupérer les paramètres de configuration. Les deux classes se trouvent dans le **Microsoft.Samples.BizTalk.WoodgroveBank.ConfigHelper** espace de noms.  
  
> [!NOTE]
>  La solution orientée services définit l'intervalle d'actualisation du cache sur 300 secondes (5  minutes). Vous pouvez aussi faire de l'intervalle d'actualisation du cache une propriété configurable dans cette solution. Cela est effectué dans la solution de gestion des processus d'entreprise. Pour plus d’informations sur la façon dont cette solution gère l’authentification unique, consultez [à l’aide de l’authentification unique efficacement dans la Solution de gestion des processus métier](../core/using-sso-efficiently-in-the-business-process-management-solution.md). Notez que, dans un tel cas, une modification de l'intervalle d'actualisation ne prend effet qu'au moment où le cache est actualisé à la fin de l'ancien intervalle.  
  
 Le **ConfigPropertyBag** présente les méthodes suivantes :  
  
|Méthode| Description|  
|------------|-----------------|  
|Lecture|Extrait une valeur pour une propriété donnée.|  
|Write|Attribue une valeur à une propriété.|  
  
 La classe utilise une instance de .NET **NameValueCollection** pour contenir les valeurs. Les deux méthodes d’accès implémentent la **IPropertyBag** de l’interface à partir de la **Microsoft.BizTalk.SSOClient.Interop** espace de noms. Le **ConfigPropertyBag** classe est une classe interne et utilisée uniquement par le **ConfigParameters** classe.  
  
> [!NOTE]
>  Les noms de clé dans le jeu de propriétés ne respectent pas la casse. Sous-jacent **NameValueCollection** utilise un hachage pas la casse et les comparaisons sans respecter la casse.  
  
 L’application utilise le **ConfigParameters** classe pour gérer les valeurs de configuration de l’authentification unique. La classe possède les méthodes publiques et attributs suivants :  
  
|Méthode ou attribut| Description|  
|-------------------------|-----------------|  
|SSOConfigParameter|Énumération pour spécifier les paramètres de configuration.|  
|GetConfigParameters|Méthode utilisée pour récupérer une valeur pour un paramètre donné. Utilise SSOConfigParameter pour indiquer le paramètre.|  
  
 Le **ConfigParameters** classe utilise la classe .NET Timer et une fonction déléguée pour configurer l’actualisation de la **ConfigPropertyBag**:  
  
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
  
 Notez que le constructeur statique initialise les variables de membres statiques, permettant ainsi l'utilisation de méthodes de classe sans créer d'instance de la classe. Le constructeur crée des instances de la banque de configuration de l’authentification unique (**ISSOConfigStore**), le jeu de propriétés de configuration (**ConfigPropertyBag**) et le verrouillage de synchronisation ( **ReaderWriterLock**) permet de contrôler l’accès à la **ConfigurationPropertyBag** pendant les mises à jour et des lectures. Le constructeur utilise ensuite **GetConfigInfo** pour récupérer les valeurs de configuration de l’authentification unique et les placer dans le jeu de propriétés. Enfin, le constructeur crée un **Timer** objet qui, après l’intervalle spécifié, appelle la fonction déléguée, **cacheRefreshCallback**.  
  
 Le **Timer** fonction déléguée est relativement simple :  
  
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
  
 Notez que la méthode de rappel d'actualisation du cache désactive le minuteur afin que la méthode puisse s'exécuter complètement. Remarquez également l'utilisation des verrous pour contrôler l'accès au jeu de propriétés. Le **ReaderWriterLock** constitue le meilleur choix ici, il est conçu pour les cas où il y a plus de lectures que d’écritures. Notez également que le verrou, **syncLock**, est statique et déclarée au niveau de la classe de niveau que tous les threads partagent la même instance de celui-ci.  
  
## <a name="using-sso-from-code"></a>Utilisation de l'authentification unique à partir du code  
 Lorsque vous utilisez l’authentification unique à partir de code, le code doit jouer le rôle de la carte : autrement dit, récupérer le ticket d’authentification unique à partir du message, échanger le ticket pour obtenir le nom d’utilisateur et un mot de passe pour le système principal et, enfin, utilisez le système principal. La solution orientée services procède par l’intermédiaire du **GetPendingTransactionsResponse** méthode de la **PendingTransactionsCaller** objet.  
  
 La méthode apparaît comme suit :  
  
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
  
 La méthode commence par récupérer les informations de configuration, notamment l'URL, pour le système principal et le nom de l'application principale (associée).  
  
 Pour échanger le ticket, la méthode doit extraire du message le ticket et le nom d'utilisateur à l'origine de la demande. Le message contient le ticket comme l’une des propriétés de contexte de message, **BTS. SSOTicket**. Pour plus d’informations, consultez **propriétés de contexte de Message** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. La méthode extrait également le **OriginatorSID** à partir des propriétés de contexte de message. Avec le ticket et le nom de l'expéditeur, la méthode appelle la méthode RedeemTicket sur le ticket pour récupérer les informations d'identification.  
  
 Le reste du code crée un cache .NET NetworkCredential pour les informations d'identification et appelle le service Web principal.  
  
> [!NOTE]
>  Comme le nom d'utilisateur et le mot de passe reviennent de l'authentification unique en texte clair, vous devez minimiser la durée de vie des variables contenant ces informations. Notez que le code déclare les variables d’informations d’identification dans un **essayez** bloc. Ici, les variables expirent à la sortie à partir de la **essayez** bloc.  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation du Service orienté solutions](../core/implementation-highlights-of-the-service-oriented-solution.md)