---
title: Optimisation des performances de IIS | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6722a2ee-3704-4aaa-9b0d-cef97bcb9a04
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93f1bca77aea5aa6c75521e46edc8fc4d01b2d73
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="optimizing-iis-performance"></a>Optimisation des performances d’IIS
## <a name="apply-iis-configuration-options-to-improve-iis-performance"></a>Appliquer les options de configuration d’IIS pour améliorer les performances d’IIS  
 Internet Information Services (IIS) expose de nombreux paramètres de configuration qui affectent les performances d’IIS. Cette rubrique décrit plusieurs de ces paramètres et fournit des indications générales pour définir les valeurs de paramètre pour améliorer les performances d’IIS.  
  
### <a name="log-only-essential-information-or-completely-disable-iis-logging"></a>Ouvrez une session uniquement les informations essentielles ou désactiver la journalisation IIS  
 Journalisation IIS doit être réduite ou même désactivée dans un environnement de production. Pour désactiver la journalisation, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le **connexions** volet, développez **Sites**, cliquez pour sélectionner le site Web pour lequel vous souhaitez désactiver la journalisation, puis activez **affichage des fonctionnalités**, puis Double-cliquez sur le **journalisation** fonctionnalité.  
  
3.  Cliquez sur **désactiver** dans les **Actions** volet pour désactiver la journalisation pour ce site Web.  
  
### <a name="disable-iis-asp-debugging-in-production-environments"></a>Désactiver le débogage des IIS ASP dans les environnements de production  
 Le débogage ASP d’IIS doit être désactivé dans un environnement de production. Pour désactiver IIS ASP débogage procédez comme suit : dans le **connexions** volet, développez **Sites**, cliquez pour sélectionner le site web pour lequel vous souhaitez désactiver le débogage ASP, activez la case à cocher **Affichage des fonctionnalités**, puis double-cliquez sur le **ASP** fonctionnalité. Cliquez pour développer **Compilation**, cliquez pour développer **propriétés de débogage**et vérifiez que les deux **activer le débogage du côté Client** et **activer côté serveur Débogage** sont définies sur **False**.  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le **connexions** volet, développez **Sites**, cliquez pour sélectionner le site web pour lequel vous souhaitez désactiver le débogage ASP, activez **affichage des fonctionnalités**, puis Double-cliquez sur le **ASP** fonctionnalité.  
  
3.  Cliquez pour développer **Compilation**, cliquez pour développer **propriétés de débogage**et vérifiez que les deux **activer le débogage du côté Client** et **activer côté serveur Débogage** sont définies sur **False**.  
  
4.  Si nécessaire, cliquez sur **appliquer** dans les **Actions** volet.  
  
 Désactiver le débogage des Applications ASP.NET et les Services Web en spécifiant le \<débogage de compilation = « false »\> section dans le fichier web.config de l’application web.  
  
### <a name="tune-the-value-of-the-asp-threads-per-processor-limit-property"></a>Régler la valeur de la propriété limite ASP de Threads par processeur  
 ASP **limite de Threads par processeur** propriété spécifie le nombre maximal de threads de travail par processeur créés par IIS. Augmentez la valeur de la limite de Threads par processeur jusqu'à ce que l’utilisation du processeur soit au moins 50 pour cent ou version ultérieure. Ce paramètre peut affecter fortement l’évolutivité de vos applications Web et les performances de votre serveur en général. Étant donné que cette propriété définit le nombre maximal de demandes ASP pouvant s’exécuter simultanément, ce paramètre doit conserver la valeur par défaut, sauf si vos applications ASP effectuent des appels de longue durée vers des composants externes. Dans ce cas, vous pouvez augmenter la valeur de limite de Threads par processeur. Ainsi, le serveur pour créer des threads supplémentaires pour gérer plus de demandes simultanées. La valeur par défaut de la limite de Threads par processeur est 25. La valeur maximale recommandée pour cette propriété est 100.  
  
 Pour augmenter la valeur de la limite de Threads par processeur, procédez comme suit : dans le **connexions** volet, sélectionnez le serveur web, puis activez **affichage des fonctionnalités**, puis double-cliquez sur le  **ASP** fonctionnalité.  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le **connexions** volet, sélectionnez le serveur web, puis activez **affichage des fonctionnalités**, puis double-cliquez sur le **ASP** fonctionnalité.  
  
3.  Cliquez pour développer **propriétés relatives aux limites** sous **comportement**, cliquez sur **limite de Threads par processeur**, entrez la valeur souhaitée pour **limite de Threads par processeur**  et cliquez sur **appliquer** dans les **Actions** volet.  
  
 Pour plus d’informations sur la façon de modifier les propriétés dans le \<limites\> élément d’IIS 7.5/7.0 \<asp\> élément, consultez [limites d’ASP. \<limites\> ](http://go.microsoft.com/fwlink/?LinkId=157483)(http://go.microsoft.com/fwlink/?LinkId=157483).  
  
> [!NOTE]  
>  Cette propriété peut uniquement être appliqué au niveau du serveur, la modification de cette propriété affecte tous les sites Web qui s’exécutent sur le serveur.  
  
### <a name="tune-the-value-of-the-asp-queue-length-property"></a>Régler la valeur de la propriété de longueur de file d’attente ASP  
 L’objectif du paramétrage de cette propriété est pour garantir des temps de réponse tout en réduisant la fréquence à laquelle le serveur envoie l’erreur HTTP 503 (serveur encombré) aux clients lorsque la file d’attente de demandes ASP est pleine. Si la valeur de propriété de longueur de file d’attente ASP est trop faible, le serveur envoie l’erreur HTTP 503 avec une fréquence supérieure. Si la valeur de propriété de longueur de file d’attente ASP est trop élevée, les utilisateurs peuvent percevoir que le serveur ne répond pas alors qu’en fait que la demande est en attente dans la file d’attente. En surveillant la file d’attente pendant les périodes de trafic élevé, vous devez discerner un modèle de pics de demande web et des creux. Notez la valeur de crête et définissez la valeur de la propriété de longueur de file d’attente ASP juste au-dessus de la valeur maximale. Utiliser la file d’attente pour gérer les pics à court terme, vérifiez les temps de réponse et limiter le système pour éviter la surcharge de subi, inattendue des pics se produisent. Si vous n’avez pas de données pour le réglage de la propriété de longueur de file d’attente ASP, un bon point de départ sera pour définir un rapport de files d’attente de 1 au nombre total de threads. Par exemple, si la propriété ASP Threads par processeur limite est définie à 25 et que vous disposez de quatre processeurs (4 * 25 = 100 threads), la valeur de la propriété de longueur de file d’attente ASP 100 et au paramétrage à partir de là.  
  
 Pour augmenter la valeur de la longueur de file d’attente de propriété, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
2.  Dans le **connexions** volet, sélectionnez le serveur Web, puis activez **affichage des fonctionnalités**, puis double-cliquez sur le **ASP** fonctionnalité.  
  
3.  Cliquez pour développer **propriétés relatives aux limites** sous **comportement**, cliquez sur **longueur de file d’attente**, entrez la valeur souhaitée pour **longueur de file d’attente** , puis Cliquez sur **appliquer** dans les **Actions** volet.  
  
 Pour plus d’informations sur la façon de modifier les propriétés dans le \<limites\> élément d’IIS 7.5/7.0 \<asp\> élément, consultez [limites d’ASP. \<limites\> ](http://go.microsoft.com/fwlink/?LinkId=157483)(http://go.microsoft.com/fwlink/?LinkId=157483).  
  
> [!NOTE]  
>  Cette propriété peut uniquement être appliqué au niveau du serveur, la modification de cette propriété affecte tous les sites Web qui s’exécutent sur le serveur.  
  
### <a name="tune-the-maxpoolthreads-registry-entry"></a>Paramétrer l’entrée de Registre MaxPoolThreads  
 Ce paramètre spécifie le nombre de threads du pool à créer par processeur. Threads de pool attendent le demandes réseau et traitent les demandes entrantes. Le compteur MaxPoolThreads n’inclut pas les threads qui sont consommés par les applications ISAPI. En règle générale, vous ne devez pas créer plus de 20 threads par processeur. MaxPoolThreads correspond à une entrée de Registre REG_DWORD située HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\InetInfo\Parameters\ avec une valeur par défaut de 4.  
  
### <a name="disable-wcf-services-tracing"></a>Désactiver les services WCF de suivi  
 Utilisez l’outil Éditeur de Configuration (SvcConfigEditor.exe) pour désactiver les services WCF de traçage dans un environnement de production. Pour plus d’informations sur l’outil Éditeur de Configuration, consultez [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](http://go.microsoft.com/fwlink/?LinkID=127070) (http://go.microsoft.com/fwlink/?LinkID=127070).  
  
### <a name="configure-aspnet-20-maxconcurrentrequests-for-iis-7570-integrated-mode"></a>Configurez ASP.NET 2.0 MaxConcurrentRequests en mode intégré de IIS 7.0/7.5  
 Lorsque ASP.NET 2.0 est hébergé sur IIS 7.5/7.0 en Mode intégré, l’utilisation de threads est gérée différemment que sur IIS 7.5/7.0 en Mode classique. Lorsque ASP.NET 2.0 est hébergé sur IIS 7.5 en mode intégré, ASP.NET 2.0 limite le nombre de demandes au lieu du nombre de threads qui s’exécutent simultanément des demandes de manière simultanée. Pour des scénarios synchrones, cela indirectement limite le nombre de threads, car le nombre de demandes sera le même que le nombre de threads. Mais pour des scénarios asynchrones, le nombre de demandes et les threads seront probablement très différent, car vous pourriez avoir beaucoup plus de requêtes que de threads. Lorsque vous exécutez ASP.NET 2.0 sur IIS 7.5 en mode intégré, les minFreeThreads minLocalRequestFreeThreads de l’élément « httpRuntime » dans le fichier machine.config sont ignorés. Pour le mode intégré d’IIS 7.5, une valeur DWORD nommé MaxConcurrentRequestsPerCPU dans HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0 détermine le nombre de requêtes simultanées par UC. Par défaut, la clé de Registre n’existe pas et le nombre de demandes par UC est limité à 12. .NET framework 3.5 SP1 inclut une mise à jour les fichiers binaires v2.0 qui prend en charge la configuration des pools d’applications IIS via le fichier aspnet.config. Cette configuration s’applique au mode intégré uniquement (le mode classique/ISAPI ignore ces paramètres). La nouvelle section de configuration aspnet.config avec les valeurs par défaut est indiquée ci-dessous :  
  
```  
<system.web>  
   <applicationPool maxConcurrentRequestsPerCPU="12" maxConcurrentThreadsPerCPU="0" requestQueueLimit="5000"/>  
</system.web>  
```  
  
 En Mode intégré de IIS 7.5, le maxWorkerThreads et maxIoThreads paramètres dans la section « processModel » du fichier machine.config ne sont pas utilisées pour régir le nombre de l’exécution de requêtes, soi, mais ils sont toujours utilisés pour régir la taille du pool de threads CLR utilisé par ASP.NET. Lorsque la section « processModel » du fichier machine.config a « autoConfig = true » (qui est le paramètre par défaut), cela donne le pool d’applications jusqu'à 100 threads de travail (MaxWorkerThreads) par processeur logique. Par conséquent, un serveur marchandise commun avec 2 processeurs double cœur aurait 400 MaxWorkerThreads. Cela doit être suffisante pour toutes les applications les plus exigeantes.  
  
 Pour plus d’informations sur la configuration de l’utilisation de Thread ASP.NET sur IIS 7.5, consultez [Blog de Thomas Marquardt sur l’utilisation de Thread ASP.NET sur IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=157518) (http://go.microsoft.com/fwlink/?LinkId=157518).  
  
### <a name="configure-aspnet-4-maxconcurrentrequests-for-iis-7570-integrated-mode"></a>Configurez ASP.NET 4 MaxConcurrentRequests en mode intégré d’IIS 7.0/7.5  
 .NET Framework 4, le paramètre par défaut pour maxConcurrentRequestsPerCPU la valeur est de 5 000, ce qui constitue un très grand nombre et par conséquent permettra beaucoup de demandes asynchrones à s’exécuter simultanément. Pour plus d’informations, consultez [ \<applicationPool\> élément (paramètres Web)](http://go.microsoft.com/fwlink/?LinkID=205339) (http://go.microsoft.com/fwlink/?LinkID=205339).  
  
 Pour le mode intégré d’IIS 7.0/7.5, une valeur DWORD nommé MaxConcurrentRequestsPerCPU dans HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0 détermine le nombre de requêtes simultanées par UC. Par défaut, la clé de Registre n’existe pas et le nombre de demandes par UC est limité à 5000.  
  
### <a name="enable-iis-http-compression"></a>Activer la compression HTTP de IIS  
 Pour utiliser plus efficacement la bande passante disponible, activez la compression HTTP de IIS. La compression HTTP fournit la durée de transmission plus rapide entre les navigateurs prenant en charge la compression et les services IIS, quelle que soit la si votre contenu est pris en charge à partir de stockage local ou d’une ressource UNC.  
  
-   **Pour configurer la compression au niveau du serveur Web :**  
  
    1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
    2.  Dans le **connexions** volet, sélectionnez le serveur Web, puis activez **affichage des fonctionnalités**, puis double-cliquez sur le **Compression** fonctionnalité.  
  
    3.  Définir les options de compression souhaité, puis **appliquer** dans les **Actions** volet.  
  
-   **Pour configurer la compression au niveau du site Web :**  
  
    1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
    2.  Dans le **connexions** volet, développez **Sites**, sélectionnez le site Web pour lequel vous souhaitez configurer la compression, sélectionnez **affichage des fonctionnalités**, et puis double-cliquez sur le **Compression** fonctionnalité.  
  
    3.  Définir les options de compression souhaité, puis **appliquer** dans les **Actions** volet.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances](../technical-guides/optimizing-performance.md)