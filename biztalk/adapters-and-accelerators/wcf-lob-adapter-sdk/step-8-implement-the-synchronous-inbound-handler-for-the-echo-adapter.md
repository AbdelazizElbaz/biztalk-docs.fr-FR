---
title: "Étape 8 : Implémenter le Gestionnaire d’entrée synchrone de l’adaptateur d’écho | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 723eac73-40c4-41b4-aca1-dd7451d25bfe
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da34bca28f073babac4907b7d408d0642a234e2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter"></a>Étape 8 : Implémenter le Gestionnaire d’entrée synchrone de l’adaptateur d’écho
![Étape 8 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")  
  
 **Durée :** 45 minutes  
  
 Dans cette étape, vous implémentez la capacité entrante de l’adaptateur de l’écho. Cette fonctionnalité permet à l’adaptateur écouter les données ou des événements à partir du système cible. Conformément à la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], vous devez uniquement implémenter la `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface, lorsque votre adaptateur prend en charge la fonctionnalité de trafic entrante. Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement la classe dérivée, appelée EchoAdpterInboundHandler pour vous.  
  
 Dans la section suivante, vous mettez à jour la classe EchoAdpterInboundHandler pour mieux comprendre comment implémenter cette interface. Lorsque vous terminez cette étape, vous avez un gestionnaire de trafic entrant de travail de l’adaptateur de l’écho.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de commencer cette étape, vous devez avoir terminé avec succès [étape 7 : implémenter le Gestionnaire de sortie synchrone pour l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md). Une connaissance élémentaire `Microsoft.ServiceModel.Channels.Common.IInboundHandler` s’avère également utile.  
  
## <a name="the-iinboundhandler-interface"></a>L’Interface IInboundHandler  
 Le `Microsoft.ServiceModel.Channels.Common.IInboundHandler` est défini en tant que :  
  
```  
public interface IInboundHandler : IConnectionHandler, IDisposable  
{  
          void StartListener(string[] actions, TimeSpan timeout);  
          void StopListener(TimeSpan timeout);  
          bool TryReceive(TimeSpan timeout, out Message message, out IInboundReply reply);  
          bool WaitForMessage(TimeSpan timeout);  
}  
```  
  
 Les descriptions de méthode sont :  
  
|Méthode| Description|  
|------------|-----------------|  
|StartListener|Démarre l’écoute des messages avec des Actions fournies WS-Addressing. Si aucun n’est spécifié, il écoute à l’ensemble ou les actions par défaut.|  
|StopListener|Arrête d’écouter.|  
|TryReceive|Tente de recevoir un message entrant à partir du système cible.|  
|WaitForMessage|Attend un message WCF entrant à partir du système cible.|  
  
 Pour plus d’informations sur la description pour les paramètres de chaque méthode, consultez la documentation sur le `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface.  
  
## <a name="implementing-the-echoadpterinboundhandler"></a>Implémentation de la EchoAdpterInboundHandler  
 L’adaptateur d’écho utilise le `System.IO.FileSystemWatcher` pour simuler le système cible. Dans l’exemple suivant, vous implémentez chaque méthode dans le `Microsoft.ServiceModel.Channels.Common.IInboundHandler` de l’interface, StartListener, StopListener, TryReceive et WaitForMessage.  
  
#### <a name="to-implement-iinboundhandler-interface-in-the-echoadpterinboundhandler-class"></a>Pour implémenter l’interface de IInboundHandler dans la classe EchoAdpterInboundHandler  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterInboundHandler.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, ajoutez les lignes suivantes à l’ensemble existant de l’utilisation de directives.  
  
    ```csharp  
    using System.IO;  
    using System.ServiceModel.Channels;  
    using System.Xml;  
    using System.Diagnostics;  
    ```  
  
3.  Ajoutez maintenant les variables de niveau classe à la classe EchoAdapterInboundHandler. Ces variables sont utilisées pour analyser le système de fichiers pour l’activité de fichier. Copiez les déclarations ci-dessous dans la classe avant le constructeur.  
  
    ```csharp  
    private Queue<Message> inboundQueue;  
    private FileSystemWatcher inboundWatcher;  
    private Object inboundQueueSynchronizationLock;  
    private string path;  
    private string filter;  
    ```  
  
4.  À l’intérieur de la méthode de constructeur EchoAdapterInboundHandler, ajoutez le code suivant pour initialiser le fichier de la surveillance d’infrastructure et capturer le chemin d’analyse et le filtre.  
  
    ```csharp  
    inboundWatcher = null;  
    inboundQueueSynchronizationLock = new Object();  
    path = connection.ConnectionFactory.Adapter.InboundFileSystemWatcherFolder;  
    filter = connection.ConnectionFactory.Adapter.InboundFileFilter;  
    ```  
  
5.  Puis ajoutez le code suivant à la **StartListener** (méthode). Le code implémente la logique pour vérifier les paramètres et démarrer l’analyse pour l’activité de fichier.  
  
    ```csharp  
    // if no actions are provided, log an error in the trace log  
    // and throw an exception  
    if (actions.Length == 0)  
    {  
        EchoAdapterUtilities.Trace.Trace(TraceEventType.Error, "http://echoadapterv2/startlistener/noactions", "No operation actions were received for listener to do specific processing.", this);  
        throw new AdapterException("Unable to receive any actions for inbound handler to start listening.");  
    }  
  
    inboundQueue = new Queue<Message>();  
    foreach (string action in actions)  
    {  
        // for the OnReceiveEcho action listen for a new file created event  
        if ("Echo/OnReceiveEcho".Equals(action))  
        {  
            if (inboundWatcher == null)  
            {  
                inboundWatcher = new FileSystemWatcher(path);  
                inboundWatcher.Filter = filter;  
                // Begin monitoring  
                inboundWatcher.EnableRaisingEvents = true;  
            }  
            inboundWatcher.Created += new FileSystemEventHandler(FileMonitor_Created);  
            EchoAdapterUtilities.Trace.Trace(TraceEventType.Information, "http://echoadapterv2/startlistener", "Listening for file created event for " + filter + " in path " + path, this);  
        }  
    }  
    ```  
  
6.  Continuer en ajoutant une implémentation pour la **StopListener** (méthode).  
  
    ```csharp  
    if (inboundWatcher != null)  
    {  
        // End monitoring  
        inboundWatcher.EnableRaisingEvents = false;  
        inboundWatcher = null;  
    }  
    lock (inboundQueueSynchronizationLock)  
    {  
        inboundQueue.Clear();  
        inboundQueue = null;  
    }  
    ```  
  
7.  Maintenant fournir une implémentation de la **TryReveive** (méthode). Cette méthode récupère le fichier le plus récent message à partir de la file d’attente interne si celle-ci est disponible.  
  
    ```csharp  
    reply = new EchoAdapterInboundReply();  
    message = null;  
    TimeoutHelper timeoutHelper = new TimeoutHelper(timeout);  
    while (true)  
    {  
        lock (inboundQueueSynchronizationLock)  
        {  
            if (inboundQueue == null)  
            {  
                //listener has been closed  
                return false;  
            }  
            if (inboundQueue.Count != 0)  
            {  
                message = inboundQueue.Dequeue();  
                if (message != null)  
                {  
                    return true;  
                }  
            }  
        }  
        if (timeoutHelper.IsExpired)  
        {  
            return false;  
        }  
        //wait for sometime, and check again  
        System.Threading.Thread.Sleep(500);  
    }  
    ```  
  
8.  Continuer en ajoutant une implémentation pour la **WaitForMessage** (méthode).  
  
    ```csharp  
    while (inboundQueue.Count == 0) { };  
    Message msg = inboundQueue.Peek();  
    if (msg != null)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
    ```  
  
9. Maintenant fournir le rappel pour l’Observateur du fichier. Pour ce faire, ajoutez la nouvelle méthode **FileMonitor_Created** à la **EchoAdapterInboundAdapter** classe.  
  
    ```csharp  
    private void FileMonitor_Created(object sender, FileSystemEventArgs e)  
    {  
        lock (inboundQueueSynchronizationLock)  
        {  
            if (e.ChangeType == WatcherChangeTypes.Created)  
            {  
                // wait for file to close - should do this in a better manner  
                System.Threading.Thread.Sleep(500);  
                try  
                {  
                    EchoAdapterUtilities.Trace.Trace(TraceEventType.Information, "http://echoadapterv2/FileMonitorCreated", "File " + e.FullPath + " created.", this);  
                    FileInfo fileInfo = new FileInfo(e.FullPath);  
                    // Create WCF message to send to the inbound service  
                    // that is listening for messages from adapter  
                    String xmlData = String.Format(@"<OnReceiveEcho xmlns=""{0}""><path>{1}</path><length>{2}</length></OnReceiveEcho>", EchoAdapter.SERVICENAMESPACE, e.FullPath, fileInfo.Length);  
                    // set action string  
                    XmlReader reader = XmlReader.Create(new StringReader(xmlData));  
                    // create WCF message  
                    Message requestMessage = Message.CreateMessage(MessageVersion.Default  
                                , "Echo/OnReceiveEcho"  
                                , reader);  
                    requestMessage.Headers.To = new Uri(path);  
                    inboundQueue.Enqueue(requestMessage);  
                }  
                catch (Exception ex)  
                {  
                    String message = String.Format("An exception was thrown while trying to open file {1}.", e.FullPath);  
                    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Error, "http://echoadapterv2/FileMonitorCreated", message, this, ex);  
                    throw new AdapterException(message, ex);  
                }  
            }  
        }  
    }  
    ```  
  
10. Maintenant que vous devez supprimer la **NotImplementedException** les exceptions levées par interne **EchoAdapterInboundReply** classe. Pour ce faire, supprimez l’instruction suivante à partir de la **abandonner** et **réponse** méthodes.  
  
    ```csharp  
    throw new NotImplementedException("The method or operation is not implemented.");  
    ```  
  
     Votre **abandonner** et **réponse** méthodes doivent être similaires à ce qui suit.  
  
    ```csharp  
    /// <summary>  
    /// Abort the inbound reply call  
    /// </summary>  
    public override void Abort()  
    {  
    }  
  
    /// <summary>  
    /// Reply message implemented  
    /// </summary>  
    public override void Reply(System.ServiceModel.Channels.Message message  
        , TimeSpan timeout)  
    {  
    }  
    ```  
  
11. Pour effectuer l’implémentation pour le Gestionnaire d’entrée, ajoutez la classe suivante au **EchoAdapterOutboundHandler.cs**. Cette classe fournit la prise en charge de délai d’attente pour l’implémentation de gestionnaire d’entrée.  
  
    ```csharp  
    /// <summary>  
    /// Utility class containing helper functions for measuring timeout   
    /// </summary>  
    class TimeoutHelper  
    {  
        private TimeSpan timeout;  
        private DateTime creationTime;  
        private Boolean isInfinite;  
  
        /// <summary>  
        /// Constructor  
        /// </summary>  
        /// <param name="timeout"></param>  
        public TimeoutHelper(TimeSpan timeout)  
        {  
            this.creationTime = DateTime.Now;  
            this.timeout = timeout;  
            if (timeout.Equals(Infinite)) this.isInfinite = true;  
        }  
  
        /// <summary>  
        /// Value of infinite timespan  
        /// </summary>  
        public static TimeSpan Infinite  
        {  
            get { return TimeSpan.MaxValue; }  
        }  
  
        /// <summary>  
        /// Value indicating remaining timeout  
        /// </summary>  
        public TimeSpan RemainingTimeout  
        {  
            get  
            {  
                if (this.isInfinite) return Infinite;  
                return this.timeout.Subtract(DateTime.Now.Subtract(this.creationTime));  
            }  
        }  
  
        /// <summary>  
        /// Get remaining timeout value and throw an exception if the timeout  
        /// has expired.  
        /// </summary>  
        /// <param name="exceptionMessage"></param>  
        /// <returns></returns>  
        public TimeSpan GetRemainingTimeoutAndThrowIfExpired(String exceptionMessage)  
        {  
            if (this.isInfinite) return Infinite;  
            if (RemainingTimeout < TimeSpan.Zero)  
            {  
                throw new TimeoutException(exceptionMessage);  
            }  
            return RemainingTimeout;  
        }  
  
        /// <summary>  
        /// Throw an exception if the timeout has expired.  
        /// </summary>  
        /// <param name="exceptionMessage"></param>  
        public void ThrowIfTimeoutExpired(String exceptionMessage)  
        {  
            if (RemainingTimeout < TimeSpan.Zero)  
            {  
                throw new TimeoutException(exceptionMessage);  
            }  
  
        }  
  
        /// <summary>  
        /// Value indicating whether timeout has expired.  
        /// </summary>  
        public Boolean IsExpired  
        {  
            get  
            {  
                if (this.isInfinite) return false;  
                return RemainingTimeout < TimeSpan.Zero;  
            }  
        }  
    }  
    ```  
  
12. Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
13. Dans le menu **Générer** , cliquez sur **Générer la solution**. Il doit compiler sans erreurs. Dans le cas contraire, vérifiez que vous avez suivi toutes les étapes ci-dessus.  
  
> [!NOTE]
>  Vous avez enregistré votre travail. Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 9 : générer et déployer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md).  
  
## <a name="what-did-i-just-do"></a>Quoi simplement ?  
 Dans cette étape du didacticiel Echo adaptateur, vous avez fourni une implémentation pour le Gestionnaire de trafic entrant. Cette implémentation fournit le fichier de la surveillance des fonctionnalités pour l’adaptateur d’écho à l’aide de la **FileSystemWatcher** classe du .NET Framework.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans l’étape suivante, vous déployez l’adaptateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 9 : Créer et déployer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md)   
 [Étape 7 : Implémenter le Gestionnaire de sortie synchrone pour l’adaptateur de l’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md)