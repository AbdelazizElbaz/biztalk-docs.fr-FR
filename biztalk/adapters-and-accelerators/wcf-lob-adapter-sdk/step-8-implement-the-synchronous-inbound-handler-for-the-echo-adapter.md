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
# <a name="step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter"></a><span data-ttu-id="fd626-102">Étape 8 : Implémenter le Gestionnaire d’entrée synchrone de l’adaptateur d’écho</span><span class="sxs-lookup"><span data-stu-id="fd626-102">Step 8: Implement the Synchronous Inbound Handler for the Echo Adapter</span></span>
<span data-ttu-id="fd626-103">![Étape 8 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")</span><span class="sxs-lookup"><span data-stu-id="fd626-103">![Step 8 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")</span></span>  
  
 <span data-ttu-id="fd626-104">**Durée :** 45 minutes</span><span class="sxs-lookup"><span data-stu-id="fd626-104">**Time to complete:** 45 minutes</span></span>  
  
 <span data-ttu-id="fd626-105">Dans cette étape, vous implémentez la capacité entrante de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="fd626-105">In this step, you implement the inbound capability of the echo adapter.</span></span> <span data-ttu-id="fd626-106">Cette fonctionnalité permet à l’adaptateur écouter les données ou des événements à partir du système cible.</span><span class="sxs-lookup"><span data-stu-id="fd626-106">This capability allows the adapter to listen for data or events from the target system.</span></span> <span data-ttu-id="fd626-107">Conformément à la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], vous devez uniquement implémenter la `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface, lorsque votre adaptateur prend en charge la fonctionnalité de trafic entrante.</span><span class="sxs-lookup"><span data-stu-id="fd626-107">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], you only need to implement the `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface, when your adapter supports inbound capability.</span></span> <span data-ttu-id="fd626-108">Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement la classe dérivée, appelée EchoAdpterInboundHandler pour vous.</span><span class="sxs-lookup"><span data-stu-id="fd626-108">The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates the derived class called EchoAdpterInboundHandler for you.</span></span>  
  
 <span data-ttu-id="fd626-109">Dans la section suivante, vous mettez à jour la classe EchoAdpterInboundHandler pour mieux comprendre comment implémenter cette interface.</span><span class="sxs-lookup"><span data-stu-id="fd626-109">In the following section, you update the EchoAdpterInboundHandler class to get a better understanding on how to implement this interface.</span></span> <span data-ttu-id="fd626-110">Lorsque vous terminez cette étape, vous avez un gestionnaire de trafic entrant de travail de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="fd626-110">When you complete this step, you have a working inbound handler for the echo adapter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fd626-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="fd626-111">Prerequisites</span></span>  
 <span data-ttu-id="fd626-112">Avant de commencer cette étape, vous devez avoir terminé avec succès [étape 7 : implémenter le Gestionnaire de sortie synchrone pour l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="fd626-112">Before you begin this step, you must have successfully completed [Step 7: Implement the Synchronous Outbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md).</span></span> <span data-ttu-id="fd626-113">Une connaissance élémentaire `Microsoft.ServiceModel.Channels.Common.IInboundHandler` s’avère également utile.</span><span class="sxs-lookup"><span data-stu-id="fd626-113">A basic familiarity with `Microsoft.ServiceModel.Channels.Common.IInboundHandler` is also helpful.</span></span>  
  
## <a name="the-iinboundhandler-interface"></a><span data-ttu-id="fd626-114">L’Interface IInboundHandler</span><span class="sxs-lookup"><span data-stu-id="fd626-114">The IInboundHandler Interface</span></span>  
 <span data-ttu-id="fd626-115">Le `Microsoft.ServiceModel.Channels.Common.IInboundHandler` est défini en tant que :</span><span class="sxs-lookup"><span data-stu-id="fd626-115">The `Microsoft.ServiceModel.Channels.Common.IInboundHandler` is defined as:</span></span>  
  
```  
public interface IInboundHandler : IConnectionHandler, IDisposable  
{  
          void StartListener(string[] actions, TimeSpan timeout);  
          void StopListener(TimeSpan timeout);  
          bool TryReceive(TimeSpan timeout, out Message message, out IInboundReply reply);  
          bool WaitForMessage(TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="fd626-116">Les descriptions de méthode sont :</span><span class="sxs-lookup"><span data-stu-id="fd626-116">The method descriptions are:</span></span>  
  
|<span data-ttu-id="fd626-117">Méthode</span><span class="sxs-lookup"><span data-stu-id="fd626-117">Method</span></span>|<span data-ttu-id="fd626-118"> Description</span><span class="sxs-lookup"><span data-stu-id="fd626-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fd626-119">StartListener</span><span class="sxs-lookup"><span data-stu-id="fd626-119">StartListener</span></span>|<span data-ttu-id="fd626-120">Démarre l’écoute des messages avec des Actions fournies WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="fd626-120">Starts listening to messages with the provided WS-Addressing Actions.</span></span> <span data-ttu-id="fd626-121">Si aucun n’est spécifié, il écoute à l’ensemble ou les actions par défaut.</span><span class="sxs-lookup"><span data-stu-id="fd626-121">If none is specified, it listens to all or the default actions.</span></span>|  
|<span data-ttu-id="fd626-122">StopListener</span><span class="sxs-lookup"><span data-stu-id="fd626-122">StopListener</span></span>|<span data-ttu-id="fd626-123">Arrête d’écouter.</span><span class="sxs-lookup"><span data-stu-id="fd626-123">Stops listening.</span></span>|  
|<span data-ttu-id="fd626-124">TryReceive</span><span class="sxs-lookup"><span data-stu-id="fd626-124">TryReceive</span></span>|<span data-ttu-id="fd626-125">Tente de recevoir un message entrant à partir du système cible.</span><span class="sxs-lookup"><span data-stu-id="fd626-125">Tries to receive an inbound message from the target system.</span></span>|  
|<span data-ttu-id="fd626-126">WaitForMessage</span><span class="sxs-lookup"><span data-stu-id="fd626-126">WaitForMessage</span></span>|<span data-ttu-id="fd626-127">Attend un message WCF entrant à partir du système cible.</span><span class="sxs-lookup"><span data-stu-id="fd626-127">Waits for an inbound WCF message from the target system.</span></span>|  
  
 <span data-ttu-id="fd626-128">Pour plus d’informations sur la description pour les paramètres de chaque méthode, consultez la documentation sur le `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface.</span><span class="sxs-lookup"><span data-stu-id="fd626-128">For more details on the description for each method parameters, see the documentation on the `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface.</span></span>  
  
## <a name="implementing-the-echoadpterinboundhandler"></a><span data-ttu-id="fd626-129">Implémentation de la EchoAdpterInboundHandler</span><span class="sxs-lookup"><span data-stu-id="fd626-129">Implementing the EchoAdpterInboundHandler</span></span>  
 <span data-ttu-id="fd626-130">L’adaptateur d’écho utilise le `System.IO.FileSystemWatcher` pour simuler le système cible.</span><span class="sxs-lookup"><span data-stu-id="fd626-130">The echo adapter uses the `System.IO.FileSystemWatcher` to simulate the target system.</span></span> <span data-ttu-id="fd626-131">Dans l’exemple suivant, vous implémentez chaque méthode dans le `Microsoft.ServiceModel.Channels.Common.IInboundHandler` de l’interface, StartListener, StopListener, TryReceive et WaitForMessage.</span><span class="sxs-lookup"><span data-stu-id="fd626-131">In the following, you implement each method within the `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface, StartListener, StopListener, TryReceive and WaitForMessage.</span></span>  
  
#### <a name="to-implement-iinboundhandler-interface-in-the-echoadpterinboundhandler-class"></a><span data-ttu-id="fd626-132">Pour implémenter l’interface de IInboundHandler dans la classe EchoAdpterInboundHandler</span><span class="sxs-lookup"><span data-stu-id="fd626-132">To implement IInboundHandler interface in the EchoAdpterInboundHandler class</span></span>  
  
1.  <span data-ttu-id="fd626-133">Dans l’Explorateur de solutions, double-cliquez sur le **EchoAdapterInboundHandler.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="fd626-133">In Solution Explorer, double-click the **EchoAdapterInboundHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="fd626-134">Dans l’éditeur Visual Studio, ajoutez les lignes suivantes à l’ensemble existant de l’utilisation de directives.</span><span class="sxs-lookup"><span data-stu-id="fd626-134">In the Visual Studio editor, add the following lines to the existing set of using directives.</span></span>  
  
    ```csharp  
    using System.IO;  
    using System.ServiceModel.Channels;  
    using System.Xml;  
    using System.Diagnostics;  
    ```  
  
3.  <span data-ttu-id="fd626-135">Ajoutez maintenant les variables de niveau classe à la classe EchoAdapterInboundHandler.</span><span class="sxs-lookup"><span data-stu-id="fd626-135">Now add class level variables to the EchoAdapterInboundHandler class.</span></span> <span data-ttu-id="fd626-136">Ces variables sont utilisées pour analyser le système de fichiers pour l’activité de fichier.</span><span class="sxs-lookup"><span data-stu-id="fd626-136">These variables are used to monitor the file system for file activity.</span></span> <span data-ttu-id="fd626-137">Copiez les déclarations ci-dessous dans la classe avant le constructeur.</span><span class="sxs-lookup"><span data-stu-id="fd626-137">Copy the declarations below into the class before the constructor.</span></span>  
  
    ```csharp  
    private Queue<Message> inboundQueue;  
    private FileSystemWatcher inboundWatcher;  
    private Object inboundQueueSynchronizationLock;  
    private string path;  
    private string filter;  
    ```  
  
4.  <span data-ttu-id="fd626-138">À l’intérieur de la méthode de constructeur EchoAdapterInboundHandler, ajoutez le code suivant pour initialiser le fichier de la surveillance d’infrastructure et capturer le chemin d’analyse et le filtre.</span><span class="sxs-lookup"><span data-stu-id="fd626-138">Inside the EchoAdapterInboundHandler constructor method, add the following code to initialize the file watching infrastructure and to capture the monitoring path and filter.</span></span>  
  
    ```csharp  
    inboundWatcher = null;  
    inboundQueueSynchronizationLock = new Object();  
    path = connection.ConnectionFactory.Adapter.InboundFileSystemWatcherFolder;  
    filter = connection.ConnectionFactory.Adapter.InboundFileFilter;  
    ```  
  
5.  <span data-ttu-id="fd626-139">Puis ajoutez le code suivant à la **StartListener** (méthode).</span><span class="sxs-lookup"><span data-stu-id="fd626-139">Now add the following code to the **StartListener** method.</span></span> <span data-ttu-id="fd626-140">Le code implémente la logique pour vérifier les paramètres et démarrer l’analyse pour l’activité de fichier.</span><span class="sxs-lookup"><span data-stu-id="fd626-140">The code implements logic to verify parameters and start monitoring for file activity.</span></span>  
  
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
  
6.  <span data-ttu-id="fd626-141">Continuer en ajoutant une implémentation pour la **StopListener** (méthode).</span><span class="sxs-lookup"><span data-stu-id="fd626-141">Continue by adding an implementation for the **StopListener** method.</span></span>  
  
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
  
7.  <span data-ttu-id="fd626-142">Maintenant fournir une implémentation de la **TryReveive** (méthode).</span><span class="sxs-lookup"><span data-stu-id="fd626-142">Now provide an implementation for the **TryReveive** method.</span></span> <span data-ttu-id="fd626-143">Cette méthode récupère le fichier le plus récent message à partir de la file d’attente interne si celle-ci est disponible.</span><span class="sxs-lookup"><span data-stu-id="fd626-143">This method retrieves the most recent file receive message from the internal queue if one is available.</span></span>  
  
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
  
8.  <span data-ttu-id="fd626-144">Continuer en ajoutant une implémentation pour la **WaitForMessage** (méthode).</span><span class="sxs-lookup"><span data-stu-id="fd626-144">Continue by adding an implementation for the **WaitForMessage** method.</span></span>  
  
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
  
9. <span data-ttu-id="fd626-145">Maintenant fournir le rappel pour l’Observateur du fichier.</span><span class="sxs-lookup"><span data-stu-id="fd626-145">Now supply the callback for the file watcher.</span></span> <span data-ttu-id="fd626-146">Pour ce faire, ajoutez la nouvelle méthode **FileMonitor_Created** à la **EchoAdapterInboundAdapter** classe.</span><span class="sxs-lookup"><span data-stu-id="fd626-146">To do so, add the new method **FileMonitor_Created** to the **EchoAdapterInboundAdapter** class.</span></span>  
  
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
  
10. <span data-ttu-id="fd626-147">Maintenant que vous devez supprimer la **NotImplementedException** les exceptions levées par interne **EchoAdapterInboundReply** classe.</span><span class="sxs-lookup"><span data-stu-id="fd626-147">Now you must remove the **NotImplementedException** exceptions thrown by the internal **EchoAdapterInboundReply** class.</span></span> <span data-ttu-id="fd626-148">Pour ce faire, supprimez l’instruction suivante à partir de la **abandonner** et **réponse** méthodes.</span><span class="sxs-lookup"><span data-stu-id="fd626-148">To do this, delete the following statement from the **Abort** and **Reply** methods.</span></span>  
  
    ```csharp  
    throw new NotImplementedException("The method or operation is not implemented.");  
    ```  
  
     <span data-ttu-id="fd626-149">Votre **abandonner** et **réponse** méthodes doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="fd626-149">Your **Abort** and **Reply** methods should be similar to the following.</span></span>  
  
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
  
11. <span data-ttu-id="fd626-150">Pour effectuer l’implémentation pour le Gestionnaire d’entrée, ajoutez la classe suivante au **EchoAdapterOutboundHandler.cs**.</span><span class="sxs-lookup"><span data-stu-id="fd626-150">To complete the implementation for the inbound handler, add the following class to **EchoAdapterOutboundHandler.cs**.</span></span> <span data-ttu-id="fd626-151">Cette classe fournit la prise en charge de délai d’attente pour l’implémentation de gestionnaire d’entrée.</span><span class="sxs-lookup"><span data-stu-id="fd626-151">This class provides timeout support for the inbound handler implementation.</span></span>  
  
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
  
12. <span data-ttu-id="fd626-152">Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="fd626-152">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
13. <span data-ttu-id="fd626-153">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="fd626-153">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="fd626-154">Il doit compiler sans erreurs.</span><span class="sxs-lookup"><span data-stu-id="fd626-154">It should compile without errors.</span></span> <span data-ttu-id="fd626-155">Dans le cas contraire, vérifiez que vous avez suivi toutes les étapes ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="fd626-155">If not, ensure that you have followed every step above.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd626-156">Vous avez enregistré votre travail.</span><span class="sxs-lookup"><span data-stu-id="fd626-156">You saved your work.</span></span> <span data-ttu-id="fd626-157">Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 9 : générer et déployer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="fd626-157">You can safely close Visual Studio at this time or go to the next step, [Step 9: Build and Deploy the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="fd626-158">Quoi simplement ?</span><span class="sxs-lookup"><span data-stu-id="fd626-158">What Did I Just Do?</span></span>  
 <span data-ttu-id="fd626-159">Dans cette étape du didacticiel Echo adaptateur, vous avez fourni une implémentation pour le Gestionnaire de trafic entrant.</span><span class="sxs-lookup"><span data-stu-id="fd626-159">In this step of the Echo Adapter tutorial, you provided an implementation for the Inbound Handler.</span></span> <span data-ttu-id="fd626-160">Cette implémentation fournit le fichier de la surveillance des fonctionnalités pour l’adaptateur d’écho à l’aide de la **FileSystemWatcher** classe du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd626-160">This implementation provides file watching capabilities for the Echo Adapter using the **FileSystemWatcher** class of the .NET Framework.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fd626-161">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fd626-161">Next Steps</span></span>  
 <span data-ttu-id="fd626-162">Dans l’étape suivante, vous déployez l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="fd626-162">In the next step, you deploy the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd626-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd626-163">See Also</span></span>  
 <span data-ttu-id="fd626-164">[Étape 9 : Créer et déployer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="fd626-164">[Step 9: Build and Deploy the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="fd626-165">Étape 7 : Implémenter le Gestionnaire de sortie synchrone pour l’adaptateur de l’écho</span><span class="sxs-lookup"><span data-stu-id="fd626-165">Step 7: Implement the Synchronous Outbound Handler for the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md)