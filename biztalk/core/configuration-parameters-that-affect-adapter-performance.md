---
title: "Les paramètres de configuration qui affectent les performances de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bbb9fb-0b31-45f0-a54c-7b2025e653b9
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46bbb5a1c796149f762ce438aed7df5c256bf465
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-parameters-that-affect-adapter-performance"></a>Paramètres de configuration qui affectent les performances des adaptateurs
Cette section décrit les paramètres de configuration qui peuvent affecter les performances des adaptateurs BizTalk Server.  
  
## <a name="clr-hosting-thread-values-for-the-host"></a>Valeurs de thread CLR Hosting de l'hôte  
 Un thread Windows étant l'unité exécutable la plus basique disponible pour un processus Windows, il est important d'en allouer suffisamment au pool de threads .NET associé à une instance d'un hôte BizTalk pour prévenir la pénurie de threads. En pareil cas, le nombre de threads disponibles ne permet pas d'effectuer la tâche demandée, ce qui peut affecter les performances. Dans le même temps, il faut veiller à n'allouer que le nombre de threads nécessaires au pool de threads .NET associé à l'hôte. L'allocation d'un nombre trop important de threads au pool de threads .NET associé à un hôte peut favoriser le basculement de contexte, risquant ainsi d'affecter les performances générales. Ce phénomène survient lorsque le noyau Windows bascule de l'exécution d'un thread à celle d'un autre thread, et peut considérablement augmenter l'utilisation de l'UC.  
  
 Modifiez le nombre de threads Windows disponibles dans le pool de threads .NET associé à une instance d'un hôte BizTalk en configurant les valeurs appropriées dans le Panneau de configuration de BizTalk Server. Pour plus d’informations sur la modification des valeurs de CLR .NET, consultez [comment modifier les paramètres .NET CLR](http://msdn.microsoft.com/library/ff629681\(v=BTS.70\).aspx).  
  
## <a name="aspnet-settings-that-can-impact-http-or-soap-adapter-performance"></a>Paramètres ASP.NET pouvant affecter les performances d'un adaptateur HTTP ou SOAP  
 Les paramètres suivants peuvent être appliquées à une application ASP.NET qui héberge une application Web qui l’adaptateur HTTP ou SOAP communique avec. Ces paramètres sont définis dans le fichier web.config ou machine.config du serveur hébergeant l'application Web. Modifiez ces paramètres pour tenir compte de la charge générée par le port d'envoi de votre adaptateur HTTP ou SOAP. Pour plus d’informations sur ces paramètres, consultez [Contention, des performances médiocres et blocages lorsque vous effectuez des demandes de service Web à partir d’applications ASP.NET](http://go.microsoft.com/fwlink/p/?LinkId=196842).  
  
|**Paramètre**|**Section du fichier de configuration**|**Valeur par défaut**|**Valeur recommandée**|  
|-------------------|---------------------------------------|-----------------------|---------------------------|  
|**minFreeThreads**<br /><br /> Nombre minimal de threads libres pour l'exécution de nouvelles demandes. ASP.NET conserve ces threads libres pour les demandes nécessitant davantage de threads pour exécuter leur traitement.|\<httpRuntime >|8|88 * nombre de processeurs sur le serveur qui héberge l’application Web.|  
|**minFreeLocalRequestFreeThreads**<br /><br /> Nombre minimal de threads libres qu'ASP.NET garde disponibles pour l'exécution de nouvelles demandes locales. Ce nombre de threads est réservé aux demandes de l'hôte local, au cas où certaines demandes émettent des demandes enfants auprès de l'hôte local dans le cadre de leur traitement. Cela permet d'éviter un blocage éventuel avec une nouvelle entrée récursive sur le serveur Web.|\<httpRuntime >|4|76 * nombre de processeurs sur le serveur hébergeant l'application Web.|  
|**executionTimeout**<br /><br /> Indique le nombre maximal de secondes pendant lequel l'exécution d'une demande est autorisée avant son arrêt automatique par ASP.NET.|\<httpRuntime >|90|90|  
|**maxconnection**<br /><br /> Détermine le nombre de connexions qui peuvent être effectuées à une adresse IP spécifique.|\<connectionManagement >|2<br /><br /> La valeur 2 pour ce paramètre est conforme à la norme RFC de l'IETF pour la spécification HTTP 1.1 et convient aux scénarios d'utilisateur, mais n'est pas optimisée pour un débit élevé.|12 * nombre de processeurs sur le serveur qui héberge l’application Web.|  
|**maxWorkerThreads**<br /><br /> Configure le nombre maximal de threads de travail à utiliser pour le processus pour chaque processeur.|\<processModel >|20|100 **Remarque :** cette valeur est implicitement multipliée par le nombre de processeurs sur le serveur.|  
|**minWorkerThreads**|\<processModel >|1|**maxWorkerThreads** / 2 **Remarque :** le paramètre minWorkerThreads n’est pas dans le fichier de configuration par défaut. Vous devez l'ajouter. **Remarque :** cette valeur est implicitement multipliée par le nombre de processeurs sur le serveur.|  
|**maxIoThreads**<br /><br /> Utilisé par ASP.NET pour limiter le nombre de threads de terminaison utilisés.|\<processModel >|20|100<br /><br /> Cette valeur est implicitement multipliée par le nombre de processeurs sur le serveur.|  
  
 Si l’ordinateur qui héberge les services Web exécute ASP.NET 2.0 ou version ultérieure, vous pouvez définir **autoConfig = true** dans la section processModel du fichier Machine.config pour configurer automatiquement les paramètres suivants pour optimiser performances en fonction de la configuration de l’ordinateur :  
  
-   Le **maxWorkerThreads** attribut.  
  
-   Le **maxIoThreads** attribut.  
  
-   Le **minFreeThreads** attribut de l’élément httpRuntime.  
  
-   Le **minLocalRequestFreeThreads** attribut de l’élément httpRuntime.  
  
-   Le **maxConnection** attribut de la \<connectionManagement > élément (paramètres réseau).  
  
> [!NOTE]
>  Le **processModel** section peut uniquement être définie dans le fichier Machine.config et affecte toutes les applications ASP.NET qui sont exécutent sur le serveur.  
  
 Pour plus d’informations sur la **processModel** élément du fichier machine.config consultez le site Web Microsoft MSDN à l’adresse [http://go.microsoft.com/fwlink/p/?LinkId=62307](http://go.microsoft.com/fwlink/p/?LinkId=62307).  
  
## <a name="registry-setting-that-governs-the-tcp-window-size"></a>Paramètre du Registre qui définit la taille de la fenêtre TCP  
 Le paramètre de Registre suivant définit la taille de fenêtre TCP qui correspond à la quantité de données reçues (en octets) pouvant être mise en mémoire tampon lors d'une connexion. Si ce paramètre n'est pas défini sur une valeur optimale, cela risque d'affecter les performances de l'adaptateur. Implémentez ce paramètre de Registre pour augmenter la taille de fenêtre TCP.  
  
> [!WARNING]
>  Si vous n'utilisez pas correctement l'Éditeur du Registre, vous risquez de provoquer de graves problèmes et de devoir réinstaller votre système d'exploitation. Microsoft ne peut pas garantir que vous parviendrez à résoudre les problèmes résultant d'une utilisation incorrecte de l'Éditeur du Registre. Son utilisation est sous votre entière responsabilité. Avant de procéder à la modification, pensez toujours à sauvegarder le Registre et à vérifier que vous connaissez la procédure de restauration de la sauvegarde en cas de problème.  
  
 Pour augmenter la taille de fenêtre TCP par défaut, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, tapez **regedit.exe**, puis cliquez sur **OK** pour démarrer l'Éditeur du Registre.  
  
     Accédez à **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\\**  
  
2.  Sous le **paramètres** de clé, créez l’entrée DWORD suivante avec la valeur indiquée.  
  
    |Entrée DWORD|Valeur par défaut|Valeur recommandée|  
    |-----------------|-------------------|-----------------------|  
    |**TcpWindowSize**<br /><br /> Ce paramètre détermine la taille de fenêtre de réception TCP maximale de l'ordinateur. La fenêtre de réception spécifie le nombre d'octets qu'un expéditeur peut transmettre sans recevoir d'accusé de réception. En général, les grandes fenêtres de réception améliorent les performances sur les réseaux à large bande passante.|17520|Définissez cette valeur sur un multiple de la taille maximale de segment (MSS, Maximum Segment Size) Ethernet compris entre 1460 et 64240. Si la mise à l'échelle des fenêtres est utilisée, définissez cette valeur sur 65535 au maximum.|  
  
    > [!NOTE]
    >  Vous devez redémarrer votre ordinateur pour que ces modifications prennent effet.  
  
3.  Fermez l'Éditeur de Registre.  
  
## <a name="see-also"></a>Voir aussi  
 [Performances et planification de capacité](../core/performance-and-capacity-planning.md)