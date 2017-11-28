---
title: "Étape 1 : Créer un Test unitaire pour soumettre des Documents à BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 688b14e4-bb16-4d12-86b8-37b8b6808472
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8016bc237b55c2404a21c91e2e68d78fdd21bcf9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-create-a-unit-test-to-submit-documents-to-biztalk-server"></a><span data-ttu-id="2b486-102">Étape 1 : Créer un Test unitaire pour soumettre des Documents à BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2b486-102">Step 1: Create a Unit Test to Submit Documents to BizTalk Server</span></span>
<span data-ttu-id="2b486-103">Serveurs d’applications ordinateur telles que BizTalk Server sont conçus pour effectuer des tâches particulières pour le compte d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="2b486-103">Computer application servers such as BizTalk Server are designed to perform particular tasks on behalf of users.</span></span> <span data-ttu-id="2b486-104">Demandes de clients envoyées au serveur d’applications en tant que messages conformes à une norme qui comprend par le serveur d’applications, via un protocole que le serveur d’applications comprend ces tâches sont lancées.</span><span class="sxs-lookup"><span data-stu-id="2b486-104">These tasks are initiated as client requests sent to the application server as messages that conform to a standard that the application server understands, via a protocol that the application server understands.</span></span> <span data-ttu-id="2b486-105">Par exemple, les clients peuvent initier le traitement des messages électroniques en envoyant des messages électroniques internet à un serveur de messagerie via le protocole SMTP.</span><span class="sxs-lookup"><span data-stu-id="2b486-105">For example, clients may initiate processing of email by sending internet e-mail messages to an email server via the SMTP protocol.</span></span> <span data-ttu-id="2b486-106">De même, les serveurs web traitent client HTML ou demandes ASP, les serveurs de base de données traitent les demandes des clients SQL et BizTalk Server puisse traiter les messages mis en forme conformément à plusieurs messages normes à l’aide de nombreux protocoles standard du client.</span><span class="sxs-lookup"><span data-stu-id="2b486-106">Likewise, web servers process client HTML or ASP requests, database servers process client SQL requests and BizTalk Server can process client messages formatted in compliance with multiple industry message standards using numerous industry standard protocols.</span></span> <span data-ttu-id="2b486-107">La capacité de charge de travail d’un serveur d’applications est généralement mesurée par le nombre de messages que le serveur d’applications peut traiter dans un laps de temps donné.</span><span class="sxs-lookup"><span data-stu-id="2b486-107">The workload capacity of an application server is typically measured by the number of messages that the application server can process in a given time period.</span></span> <span data-ttu-id="2b486-108">La capacité de charge de travail de BizTalk Server est de même mesurée comme le nombre moyen de « documents reçus par seconde », « documents traités par seconde » et/ou « orchestrations réussies par seconde » sur une période prolongée, par exemple une journée de travail occupée ou même un semaine de travail.</span><span class="sxs-lookup"><span data-stu-id="2b486-108">The workload capacity of BizTalk Server is likewise measured as the average number of “documents received per second”, “documents processed per second” and/or “orchestrations completed per second” over an extended period of time, such as a busy workday or even a work week.</span></span> <span data-ttu-id="2b486-109">Les fonctionnalités de test de charge Visual Studio 2010 peuvent de simuler un profil de charge de plusieurs centaines d’utilisateurs accédant simultanément à une application serveur.</span><span class="sxs-lookup"><span data-stu-id="2b486-109">Visual Studio 2010 load test functionality can simulate a load profile of up to hundreds of users simultaneously accessing a server application.</span></span> <span data-ttu-id="2b486-110">Cette fonctionnalité de test de charge fournit des métriques en temps réel pour les indicateurs de performance clé sélectionné, ainsi que la capacité de stocker ces mesures dans une base de données pour une analyse future.</span><span class="sxs-lookup"><span data-stu-id="2b486-110">This load testing functionality provides real time metrics for selected key performance indicators as well as the ability to store these metrics in a database for future analysis.</span></span> <span data-ttu-id="2b486-111">Ce document de décrit l’utilisation de projets de Test Visual Studio à des fins de test d’une application BizTalk Server, notamment comment créer une unité de charge des tests, comment créer des tests de charge et comment configurer les tests de charge pour la capture de données de compteur de performances requis pour déterminer le nombre maximal durable débit acceptable d’une application BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2b486-111">This document desribes the use of Visual Studio Test projects for the purpose of load testing a BizTalk Server application, including how to create unit tests, how to create load tests and how to configure load tests to capture performance counter data required to determine the Maximum Sustainable Throughput (MST) of a BizTalk Server application.</span></span>  
  
## <a name="creating-a-visual-studio-unit-test-to-submit-documents-to-biztalk-server"></a><span data-ttu-id="2b486-112">Création d’un Test unitaire de Visual Studio pour soumettre des Documents à BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2b486-112">Creating a Visual Studio Unit Test to Submit Documents to BizTalk Server</span></span>  
 <span data-ttu-id="2b486-113">Fait référence à un test unitaire de Visual Studio le [Microsoft.VisualStudio.TestTools.UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) espace de noms (http://go.microsoft.com/fwlink/?LinkID=132293) qui fournit plusieurs classes qui fournissent la prise en charge pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="2b486-113">A Visual Studio Unit test references the [Microsoft.VisualStudio.TestTools.UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) (http://go.microsoft.com/fwlink/?LinkID=132293) namespace which supplies several classes that provide support for unit testing.</span></span> <span data-ttu-id="2b486-114">Une importance particulière, le [UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) (http://go.Microsoft.com/fwlink/?) LinkID = 132293) espace de noms inclut la [Microsoft.VisualStudio.TestTools.UnitTesting.TestContext](http://go.microsoft.com/fwlink/?LinkID=208233) (http://go.Microsoft.com/fwlink/?) LinkID = 208233) classe pour stocker les informations fournies pour les tests unitaires et la [Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute](http://go.microsoft.com/fwlink/?LinkID=208235) (http://go.Microsoft.com/fwlink/?) LinkID = 208235) classe est utilisée pour définir des méthodes de Test.</span><span class="sxs-lookup"><span data-stu-id="2b486-114">Of particular importance, the [UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) (http://go.microsoft.com/fwlink/?LinkID=132293) namespace includes the [Microsoft.VisualStudio.TestTools.UnitTesting.TestContext](http://go.microsoft.com/fwlink/?LinkID=208233) (http://go.microsoft.com/fwlink/?LinkID=208233) class to store information provided to Unit tests and the [Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute](http://go.microsoft.com/fwlink/?LinkID=208235) (http://go.microsoft.com/fwlink/?LinkID=208235) class is used to define Test methods.</span></span> <span data-ttu-id="2b486-115">Pour des raisons de BizTalk Server de test de charge, les méthodes de Test doivent indiquer le message doit être chargé et le point de terminaison/URL à laquelle le message doit être envoyé.</span><span class="sxs-lookup"><span data-stu-id="2b486-115">For purposes of load testing BizTalk Server, Test methods should specify the message to be loaded and the endpoint/URL to which the message should be sent.</span></span> <span data-ttu-id="2b486-116">L’URL de point de terminaison/servira ensuite en tant que point d’entrée de message dans BizTalk Server lors de l’emplacement de réception BizTalk correspondant est créé.</span><span class="sxs-lookup"><span data-stu-id="2b486-116">The endpoint/URL will then serve as the message entry point into BizTalk Server when a corresponding BizTalk receive location is created.</span></span>  
  
 <span data-ttu-id="2b486-117">À des fins d’illustration, l’exemple de code dans cette rubrique décrit les méthodes de Test qui utilisent la [System.ServiceModel.ChannelFactory(TChannel)](http://go.microsoft.com/fwlink/?LinkId=208238) (http://go.Microsoft.com/fwlink/?) LinkID = 208238) pour envoyer des messages aux points de terminaison de service qui utilisent le point de terminaison WCF net.tcp et qui sont surveillés par BizTalk WCF-Custom classe d’adaptateur de réception.</span><span class="sxs-lookup"><span data-stu-id="2b486-117">For purposes of illustration, the sample code in this topic describes Test methods which utilize the [System.ServiceModel.ChannelFactory(TChannel)](http://go.microsoft.com/fwlink/?LinkId=208238) (http://go.microsoft.com/fwlink/?LinkID=208238) class to send messages to service endpoints that use the WCF net.tcp endpoint and are monitored by the BizTalk WCF-Custom receive adapter.</span></span> <span data-ttu-id="2b486-118">Points de terminaison de service pour les messages de test sont définis dans le fichier de Configuration de l’Application (app.config) du projet de Test.</span><span class="sxs-lookup"><span data-stu-id="2b486-118">Service endpoints for test messages are defined in the Application Configuration (app.config) file of the Test project.</span></span>  
  
 <span data-ttu-id="2b486-119">Pour plus d’informations sur les Tests unitaires Visual Studio, consultez [Anatomie d’un Test unitaire](http://go.microsoft.com/fwlink/?LinkID=208232) (http://go.microsoft.com/fwlink/?LinkID=208232).</span><span class="sxs-lookup"><span data-stu-id="2b486-119">For more information about Visual Studio Unit Tests see [Anatomy of a Unit Test](http://go.microsoft.com/fwlink/?LinkID=208232) (http://go.microsoft.com/fwlink/?LinkID=208232).</span></span>  
  
 <span data-ttu-id="2b486-120">Suivez les étapes décrites dans les sections ci-dessous pour créer un projet de Test avec un Test unitaire pour soumettre des documents à un ou plusieurs ordinateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2b486-120">Follow the steps in the sections below to create a Test project with a Unit Test to submit documents to one or more BizTalk Server computers.</span></span> <span data-ttu-id="2b486-121">Ces étapes ont été effectués à l’aide de Visual Studio 2010 Ultimate édition.</span><span class="sxs-lookup"><span data-stu-id="2b486-121">These steps were completed using Visual Studio 2010 Ultimate Edition.</span></span>  
  
### <a name="set-visual-studio-2010-test-project-options"></a><span data-ttu-id="2b486-122">Définir les Options de projet de Test Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="2b486-122">Set Visual Studio 2010 Test Project Options</span></span>  
  
1.  <span data-ttu-id="2b486-123">Lancez Visual Studio 2010 Ultimate édition.</span><span class="sxs-lookup"><span data-stu-id="2b486-123">Launch Visual Studio 2010 Ultimate edition.</span></span> <span data-ttu-id="2b486-124">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Visual Studio 2010** puis cliquez sur **Microsoft Visual Studio 2010**.</span><span class="sxs-lookup"><span data-stu-id="2b486-124">Click **Start**, point to **All Programs**, point to **Microsoft Visual Studio 2010** and then click **Microsoft Visual Studio 2010**.</span></span>  
  
2.  <span data-ttu-id="2b486-125">Dans Visual Studio 2010, cliquez sur **outils** puis cliquez sur **Options** pour afficher les **Options** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2b486-125">In Visual Studio 2010, click **Tools** and then click **Options** to display the **Options** dialog box.</span></span>  
  
3.  <span data-ttu-id="2b486-126">Cliquez pour développer **outils de Test** puis cliquez sur **un projet de Test** pour afficher les options pour la création de nouveaux projets de test.</span><span class="sxs-lookup"><span data-stu-id="2b486-126">Click to expand **Test Tools** and then click **Test Project** to display options for creation of new test projects.</span></span>  
  
4.  <span data-ttu-id="2b486-127">Définir le **langage de projet de test par défaut :** à **le projet de test Visual c#**.</span><span class="sxs-lookup"><span data-stu-id="2b486-127">Set the **Default test project language:** to **Visual C# test project**.</span></span>  
  
5.  <span data-ttu-id="2b486-128">Sous l’option à **sélectionner les fichiers qui seront ajoutés à chaque nouveau projet de test par défaut :** sélectionnez **le projet de test Visual c#**et désactivez tous les types de test pour Visual c# de projets à l’exception des detest **Test unitaire**.</span><span class="sxs-lookup"><span data-stu-id="2b486-128">Under the option to **Select the files that will be added to each new test project, by default:** select **Visual C# test project**, and uncheck all of the test types for Visual C# test projects except for **Unit Test**.</span></span>  
  
6.  <span data-ttu-id="2b486-129">Cliquez sur **OK** pour fermer la boîte de dialogue **Options** .</span><span class="sxs-lookup"><span data-stu-id="2b486-129">Click **OK** to close the **Options** dialog box.</span></span>  
  
### <a name="create-a-new-visual-studio-2010-solution-with-a-test-project"></a><span data-ttu-id="2b486-130">Créer une nouvelle Solution Visual Studio 2010 avec un projet de Test</span><span class="sxs-lookup"><span data-stu-id="2b486-130">Create a new Visual Studio 2010 Solution with a Test Project</span></span>  
  
1.  <span data-ttu-id="2b486-131">Créez le dossier **C:\Projects** sur l’ordinateur Visual Studio 2010 Ultimate.</span><span class="sxs-lookup"><span data-stu-id="2b486-131">Create the folder **C:\Projects** on the Visual Studio 2010 Ultimate computer.</span></span>  
  
2.  <span data-ttu-id="2b486-132">Dans Visual Studio 2010, cliquez sur **fichier**, pointez sur **nouveau**, puis cliquez sur **projet** pour afficher les **nouveau projet** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2b486-132">In Visual Studio 2010 click **File**, point to **New**, and click **Project** to display the **New Project** dialog box.</span></span>  
  
3.  <span data-ttu-id="2b486-133">Sous **modèles installés** cliquez pour développer **Visual C#**, puis cliquez sur **Test**.</span><span class="sxs-lookup"><span data-stu-id="2b486-133">Under **Installed Templates** click to expand **Visual C#**, and click **Test**.</span></span>  
  
4.  <span data-ttu-id="2b486-134">Au bas de la **nouveau projet** boîte de dialogue spécifier les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="2b486-134">At the bottom of the **New Project** dialog box specify the following options:</span></span>  
  
    -   <span data-ttu-id="2b486-135">**Nom :**</span><span class="sxs-lookup"><span data-stu-id="2b486-135">**Name:**</span></span>  
         <span data-ttu-id="2b486-136">**BTSLoad**</span><span class="sxs-lookup"><span data-stu-id="2b486-136">**BTSLoad**</span></span>  
  
    -   <span data-ttu-id="2b486-137">**Emplacement :**</span><span class="sxs-lookup"><span data-stu-id="2b486-137">**Location:**</span></span>  
         <span data-ttu-id="2b486-138">**C:\projects\\**</span><span class="sxs-lookup"><span data-stu-id="2b486-138">**C:\Projects\\**</span></span>  
  
    -   <span data-ttu-id="2b486-139">**Nom de la solution :**</span><span class="sxs-lookup"><span data-stu-id="2b486-139">**Solution name:**</span></span>  
         <span data-ttu-id="2b486-140">**Test de charge**</span><span class="sxs-lookup"><span data-stu-id="2b486-140">**LoadTest**</span></span>  
  
5.  <span data-ttu-id="2b486-141">Assurez-vous que l’option à **créer le répertoire pour la solution** est activée, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2b486-141">Ensure that the option to **Create directory for solution** is checked and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="2b486-142">Ajouter un dossier dans le projet BTSLoad ; ce dossier contient les messages de test à être soumis à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2b486-142">Add a folder to the BTSLoad project; this folder will contain test messages to be submitted to BizTalk Server.</span></span> <span data-ttu-id="2b486-143">Dans l’Explorateur de solutions, cliquez sur le projet BTSLoad, pointez sur **ajouter**, puis cliquez sur **nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="2b486-143">In Solution Explorer, right-click the BTSLoad project, point to **Add**, and click **New Folder**.</span></span> <span data-ttu-id="2b486-144">Une icône de dossier avec le texte mis en surbrillance **Nouveaudossier1** s’affiche sous le projet BTSLoad, type **TestMessages** pour modifier le texte mis en surbrillance et appuyez sur la **entrée** clé Pour créer le dossier C:\Projects\LoadTest\BTSLoad\TestMessages.</span><span class="sxs-lookup"><span data-stu-id="2b486-144">A folder icon with the highlighted text **NewFolder1** will appear under the BTSLoad project, type **TestMessages** to change the highlighted text and press the **Enter** key to create the folder C:\Projects\LoadTest\BTSLoad\TestMessages.</span></span>  
  
### <a name="update-the-code-in-the-test-project-and-add-an-application-configuration-file-to-the-test-project"></a><span data-ttu-id="2b486-145">Mettre à jour le Code dans le projet de Test et ajouter un fichier de Configuration d’Application au projet de Test</span><span class="sxs-lookup"><span data-stu-id="2b486-145">Update the Code in the Test Project and add an Application Configuration File to the Test Project</span></span>  
  
1.  <span data-ttu-id="2b486-146">Dans l’Explorateur de solutions sélectionnez **UnitTest1.cs** et remplacez le code existant par l’exemple de liste de code suivante :</span><span class="sxs-lookup"><span data-stu-id="2b486-146">In Solution Explorer click to select **UnitTest1.cs** and replace the existing code with the following sample code listing:</span></span>  
  
    ```csharp  
    #region Using Directives  
    using System;  
    using System.IO;  
    using System.Diagnostics;  
    using System.Text;  
    using System.Configuration;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Xml;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
    #endregion  
  
    namespace Microsoft.BizTalk.Samples  
    {  
        [TestClass]  
        public class BTSLoadTest  
        {  
            #region Constants  
            private const int MaxBufferSize = 2097152;  
            private const string Source = "BTS Load Test";  
            private const string Star = "*";  
            private const string TestMessageFolderParameter = "testMessageFolder";  
            private const string TestMessageFolderDefault = @"C:\Projects\LoadTest\BTSLoad\TestMessages";  
            private const string TestMessageFolderFormat = @"Test Message Folder = {0}";  
            private const string TestXmlDocument = "testxmldocument.xml";  
            #endregion  
  
            #region Private Instance Fields  
            private TestContext testContextInstance;  
            #endregion  
  
            #region Private ThreadStatic Fields  
            [ThreadStatic]  
            private static ChannelFactory<IRequestChannel> channelFactory;  
            [ThreadStatic]  
            private static IRequestChannel channel = null;  
            [ThreadStatic]  
            private static byte[] buffer = null;  
            #endregion  
  
            #region Private Static Fields  
            private static string testMessageFolder = null;  
            #endregion  
  
            #region Public Instance Constructor  
            public BTSLoadTest()  
            {  
            }  
            #endregion  
  
            #region Public Static Constructor  
            static BTSLoadTest()  
            {  
                try  
                {  
                    testMessageFolder = ConfigurationManager.AppSettings[TestMessageFolderParameter];  
                    if (string.IsNullOrEmpty(testMessageFolder))  
                    {  
                        testMessageFolder = TestMessageFolderDefault;  
                    }  
                }  
                catch (Exception ex)  
                {  
                    Trace.WriteLine(ex.Message);  
                    EventLog.WriteEntry(Source, ex.Message, EventLogEntryType.Error);  
                }  
            }  
            #endregion  
  
            #region Public Properties  
            /// <summary>  
            ///Gets or sets the test context which provides  
            ///information about and functionality for the current test run.  
            ///</summary>  
            public TestContext TestContext  
            {  
                get  
                {  
                    return testContextInstance;  
                }  
                set  
                {  
                    testContextInstance = value;  
                }  
            }  
            #endregion  
  
            #region Test Methods  
  
            [TestMethod]  
            public void BTSMessaging()  
            {  
                InvokeBizTalkReceiveLocation("BTSMessagingEP",  
                                               testMessageFolder,  
                                               TestXmlDocument,  
                                               MessageVersion.Default,  
                                               SessionMode.Allowed);  
            }  
  
            [TestMethod]  
            public void BTSMessaging2()  
            {  
                InvokeBizTalkReceiveLocation("BTSMessagingEP2",  
                                               testMessageFolder,  
                                               TestXmlDocument,  
                                               MessageVersion.Default,  
                                               SessionMode.Allowed);  
            }  
  
            [TestMethod]  
            public void BTSOrchestration()  
            {  
                InvokeBizTalkReceiveLocation("BTSOrchestrationEP",  
                                               testMessageFolder,  
                                               TestXmlDocument,  
                                               MessageVersion.Default,  
                                               SessionMode.Allowed);  
            }  
            #endregion  
  
            #region Helper Methods  
            public void InvokeBizTalkReceiveLocation(string endpointConfigurationName,  
                                               string requestMessageFolder,  
                                               string requestMessageName,  
                                               MessageVersion messageVersion,  
                                               SessionMode sessionMode)  
            {  
                XmlTextReader xmlTextReader = null;  
                Message requestMessage = null;  
                Message responseMessage = null;  
  
                try  
                {  
                    if (channel == null || channel.State != CommunicationState.Opened)  
                    {  
                        channelFactory = new ChannelFactory<IRequestChannel>(endpointConfigurationName);  
                        channelFactory.Endpoint.Contract.SessionMode = sessionMode;  
                        channel = channelFactory.CreateChannel();  
                    }  
                    if (buffer == null)  
                    {  
                        string path = Path.Combine(requestMessageFolder, requestMessageName);  
  
                        string message;  
                        using (StreamReader reader = new StreamReader(File.Open(path, FileMode.Open, FileAccess.Read, FileShare.Read)))  
                        {  
                            message = reader.ReadToEnd();  
                        }  
                        buffer = Encoding.UTF8.GetBytes(message);  
                    }  
                    MemoryStream stream = new MemoryStream(buffer);  
                    xmlTextReader = new XmlTextReader(stream);  
                    requestMessage = Message.CreateMessage(messageVersion, Star, xmlTextReader);  
                    TestContext.BeginTimer(requestMessageName);  
                    responseMessage = channel.Request(requestMessage);  
                }  
                catch (FaultException ex)  
                {  
                    HandleException(ex);  
                    throw;  
                }  
                catch (CommunicationException ex)  
                {  
                    HandleException(ex);  
                    throw;  
                }  
                catch (TimeoutException ex)  
                {  
                    HandleException(ex);  
                    throw;  
                }  
                catch (Exception ex)  
                {  
                    HandleException(ex);  
                    throw;  
                }  
                finally  
                {  
                    TestContext.EndTimer(requestMessageName);  
                    CloseObjects(xmlTextReader,  
                                 requestMessage,  
                                 responseMessage);  
                }  
            }  
  
            private void HandleException(Exception ex)  
            {  
                try  
                {  
                    Trace.WriteLine(ex.Message);  
                    EventLog.WriteEntry(Source, ex.Message, EventLogEntryType.Error);  
                }  
                catch (Exception)  
                {  
                }  
            }  
  
            private void CloseObjects(XmlTextReader xmlTextReader,  
                               Message requestMessage,  
                               Message responseMessage)  
            {  
                try  
                {  
                    if (xmlTextReader != null)  
                    {  
                        xmlTextReader.Close();  
                    }  
                    if (requestMessage != null)  
                    {  
                        requestMessage.Close();  
                    }  
                    if (responseMessage != null)  
                    {  
                        responseMessage.Close();  
                    }  
                }  
                catch (Exception)  
                {  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="2b486-147">Ajoutez un fichier de Configuration de l’Application au projet de Test :</span><span class="sxs-lookup"><span data-stu-id="2b486-147">Add an Application Configuration file to the Test project:</span></span>  
  
    1.  <span data-ttu-id="2b486-148">Dans l’Explorateur de solutions, cliquez sur le projet BTSLoad, pointez sur **ajouter** et cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="2b486-148">In Solution Explorer, right-click the BTSLoad project, point to **Add** and click **New item**.</span></span>  
  
    2.  <span data-ttu-id="2b486-149">Dans le **ajouter un nouvel élément** boîte de dialogue **modèles installés**, cliquez sur **général**.</span><span class="sxs-lookup"><span data-stu-id="2b486-149">In the **Add New Item** dialog box, under **Installed Templates**, click **General**.</span></span>  
  
    3.  <span data-ttu-id="2b486-150">Dans la liste des éléments qui sont affichés sélectionnez **fichier de Configuration d’Application** puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="2b486-150">In the list of items that are displayed click to select **Application Configuration File** and then click **Add**.</span></span>  
  
    4.  <span data-ttu-id="2b486-151">Dans l’Explorateur de solutions, sélectionnez le fichier app.config et remplacez le contenu du fichier app.config avec l’exemple de code sous :</span><span class="sxs-lookup"><span data-stu-id="2b486-151">In Solution Explorer select the app.config file and replace the contents of the app.config file with the sample code listing below:</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="2b486-152">Pour chaque point de terminaison client défini dans ce fichier, *ordinateur BizTalk Server* est un espace réservé pour le nom réel de l’ou les ordinateurs que vous effectuerez chargement de test par rapport à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2b486-152">For each client endpoint defined in this file, *BizTalk Server Computer* is a placeholder for the actual name of the BizTalk Server computer(s) that you will perform load testing against.</span></span>  
  
        ```xml  
  
        <configuration>  
          <system.serviceModel>  
            <!-- Bindings used by client endpoints -->  
            <bindings>  
              <netTcpBinding>  
                <binding name="netTcpBinding" closeTimeout="01:10:00" openTimeout="01:10:00" receiveTimeout="01:10:00" sendTimeout="01:10:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="100" maxBufferPoolSize="1048576" maxBufferSize="10485760" maxConnections="400" maxReceivedMessageSize="10485760">  
                  <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384" />  
                  <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false" />  
                  <security mode="None">  
                    <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
                    <message clientCredentialType="Windows" />  
                  </security>  
                </binding>  
              </netTcpBinding>  
            </bindings>  
            <client>  
              <!-- Client endpoints used to exchange messages with WCF Receive Locations -->  
  
              <!-- BTSMessagingEP -->  
              <endpoint address="net.tcp://BizTalk Server Computer:8123/btsloadtest" binding="netTcpBinding" bindingConfiguration="netTcpBinding" contract="System.ServiceModel.Channels.IRequestChannel" name="BTSMessagingEP" />  
              <endpoint address="net.tcp://BizTalk Server Computer:8123/btsloadtest" binding="netTcpBinding" bindingConfiguration="netTcpBinding" contract="System.ServiceModel.Channels.IRequestChannel" name="BTSMessagingEP" />  
  
              <!-- BTSOrchestrationEP -->  
              <endpoint address="net.tcp://BizTalk Server Computer:8122/btsloadtest" binding="netTcpBinding" bindingConfiguration="netTcpBinding" contract="System.ServiceModel.Channels.IRequestChannel" name="BTSOrchestrationEP" />  
            </client>  
          </system.serviceModel>  
          <appSettings>  
            <!-- Folder containing test messages -->  
            <add key="testMessageFolder" value="C:\Projects\LoadTest\BTSLoad\TestMessages" />  
            <add key="ClientSettingsProvider.ServiceUri" value="" />  
          </appSettings>  
        </configuration>  
        ```  
  
    5.  <span data-ttu-id="2b486-153">Cliquez sur le **fichier** menu dans Visual Studio 2010, puis cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="2b486-153">Click the **File** menu in Visual Studio 2010 and then click **Save All**.</span></span>  
  
### <a name="add-a-test-message-to-the-project"></a><span data-ttu-id="2b486-154">Ajouter un Message de Test au projet</span><span class="sxs-lookup"><span data-stu-id="2b486-154">Add a Test Message to the Project</span></span>  
 <span data-ttu-id="2b486-155">Pour des raisons de cet exemple, BizTalk Server emplacements de réception et envoi du port (s) est configuré pour utiliser passent par les pipelines et n’effectue aucune validation de document.</span><span class="sxs-lookup"><span data-stu-id="2b486-155">For purposes of this example, BizTalk Server receive location(s) and send port(s) will be configured to use pass through pipelines and will not perform any document validation.</span></span> <span data-ttu-id="2b486-156">Suivez ces étapes pour ajouter un message de test au projet :</span><span class="sxs-lookup"><span data-stu-id="2b486-156">Follow these steps to add a test message to the project:</span></span>  
  
1.  <span data-ttu-id="2b486-157">Lancez le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="2b486-157">Launch Notepad.</span></span> <span data-ttu-id="2b486-158">Cliquez sur **Démarrer**, cliquez sur **exécuter** et type **bloc-notes** dans les **exécuter** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2b486-158">Click **Start**, click **Run** and type **Notepad** in the **Run** dialog box.</span></span>  
  
2.  <span data-ttu-id="2b486-159">Copiez le texte suivant dans le bloc-notes et l’enregistrer en tant que « C:\Projects\LoadTest\BTSLoad\TestMessages\TestXmlDocument.xml »</span><span class="sxs-lookup"><span data-stu-id="2b486-159">Copy the following text into Notepad and save as “C:\Projects\LoadTest\BTSLoad\TestMessages\TestXmlDocument.xml”</span></span>  
  
    ```  
    <BTSLoadTest xmlns="http://Microsoft.BizTalk.Samples.BTSLoadTest">  
    <MessageText>  
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    This is sample message text. This is sample message text. This is sample message text. This is sample message text.   
    </MessageText>  
    </BTSLoadTest>  
    ```  
  
3.  <span data-ttu-id="2b486-160">Fermez le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="2b486-160">Close Notepad.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2b486-161">Ce fichier sera doivent être enregistrés pour le même chemin d’accès à l’aide du même nom sur chaque ordinateur Agent de Test de charge si plusieurs ordinateurs de l’Agent de Test de charge sont utilisés pour le test de charge.</span><span class="sxs-lookup"><span data-stu-id="2b486-161">This file will need to be saved to the same path using the same file name on every Load Test Agent computer if multiple Load Test Agent computers are used for load testing.</span></span>  
  
### <a name="add-necessary-references-to-the-project-and-build-the-test-project"></a><span data-ttu-id="2b486-162">Ajouter les références nécessaires au projet et générez le projet de Test</span><span class="sxs-lookup"><span data-stu-id="2b486-162">Add Necessary References to the Project and Build the Test Project</span></span>  
  
1.  <span data-ttu-id="2b486-163">Dans l’Explorateur de solutions, cliquez sur le **références** dossier pour le projet de BTSLoad, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="2b486-163">In Solution Explorer, right-click the **References** folder for the BTSLoad project and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="2b486-164">Dans la boîte de dialogue Ajouter une référence, cliquez sur le **.NET** onglet et utiliser la combinaison de la souris et clavier CTRL + clic pour sélectionner simultanément des espaces de noms .NET suivants :</span><span class="sxs-lookup"><span data-stu-id="2b486-164">In the Add Reference dialog box, click the **.NET** tab and use the CTRL+Click keyboard/mouse combination to simultaneously select the following .NET namespaces:</span></span>  
  
    -   <span data-ttu-id="2b486-165">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="2b486-165">System.Configuration</span></span>  
  
    -   <span data-ttu-id="2b486-166">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="2b486-166">System.Runtime.Serialization</span></span>  
  
    -   <span data-ttu-id="2b486-167">System.ServiceModel.Channels</span><span class="sxs-lookup"><span data-stu-id="2b486-167">System.ServiceModel.Channels</span></span>  
  
    -   <span data-ttu-id="2b486-168">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2b486-168">System.ServiceModel</span></span>  
  
    -   <span data-ttu-id="2b486-169">System.Web.Extensions</span><span class="sxs-lookup"><span data-stu-id="2b486-169">System.Web.Extensions</span></span>  
  
    -   <span data-ttu-id="2b486-170">System.Xml</span><span class="sxs-lookup"><span data-stu-id="2b486-170">System.Xml</span></span>  
  
3.  <span data-ttu-id="2b486-171">Après avoir sélectionné les espaces de noms, cliquez sur **OK** pour ajouter ces assemblys en tant que références au projet de Test de BTSLoad.</span><span class="sxs-lookup"><span data-stu-id="2b486-171">After selecting the namespaces click **OK** to add these assemblies as references to the BTSLoad Test project.</span></span>  
  
4.  <span data-ttu-id="2b486-172">Bouton droit sur le **BTSLoad** de projet, puis cliquez sur **générer** pour compiler le projet dans l’assembly BTSLoad.</span><span class="sxs-lookup"><span data-stu-id="2b486-172">Right click the **BTSLoad** project and then click **Build** to compile the project into the BTSLoad assembly.</span></span>