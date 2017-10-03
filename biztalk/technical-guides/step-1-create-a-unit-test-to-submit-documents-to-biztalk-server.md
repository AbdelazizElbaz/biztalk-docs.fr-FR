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
# <a name="step-1-create-a-unit-test-to-submit-documents-to-biztalk-server"></a>Étape 1 : Créer un Test unitaire pour soumettre des Documents à BizTalk Server
Serveurs d’applications ordinateur telles que BizTalk Server sont conçus pour effectuer des tâches particulières pour le compte d’utilisateurs. Demandes de clients envoyées au serveur d’applications en tant que messages conformes à une norme qui comprend par le serveur d’applications, via un protocole que le serveur d’applications comprend ces tâches sont lancées. Par exemple, les clients peuvent initier le traitement des messages électroniques en envoyant des messages électroniques internet à un serveur de messagerie via le protocole SMTP. De même, les serveurs web traitent client HTML ou demandes ASP, les serveurs de base de données traitent les demandes des clients SQL et BizTalk Server puisse traiter les messages mis en forme conformément à plusieurs messages normes à l’aide de nombreux protocoles standard du client. La capacité de charge de travail d’un serveur d’applications est généralement mesurée par le nombre de messages que le serveur d’applications peut traiter dans un laps de temps donné. La capacité de charge de travail de BizTalk Server est de même mesurée comme le nombre moyen de « documents reçus par seconde », « documents traités par seconde » et/ou « orchestrations réussies par seconde » sur une période prolongée, par exemple une journée de travail occupée ou même un semaine de travail. Les fonctionnalités de test de charge Visual Studio 2010 peuvent de simuler un profil de charge de plusieurs centaines d’utilisateurs accédant simultanément à une application serveur. Cette fonctionnalité de test de charge fournit des métriques en temps réel pour les indicateurs de performance clé sélectionné, ainsi que la capacité de stocker ces mesures dans une base de données pour une analyse future. Ce document de décrit l’utilisation de projets de Test Visual Studio à des fins de test d’une application BizTalk Server, notamment comment créer une unité de charge des tests, comment créer des tests de charge et comment configurer les tests de charge pour la capture de données de compteur de performances requis pour déterminer le nombre maximal durable débit acceptable d’une application BizTalk Server.  
  
## <a name="creating-a-visual-studio-unit-test-to-submit-documents-to-biztalk-server"></a>Création d’un Test unitaire de Visual Studio pour soumettre des Documents à BizTalk Server  
 Fait référence à un test unitaire de Visual Studio le [Microsoft.VisualStudio.TestTools.UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) espace de noms (http://go.microsoft.com/fwlink/?LinkID=132293) qui fournit plusieurs classes qui fournissent la prise en charge pour les tests unitaires. Une importance particulière, le [UnitTesting](http://go.microsoft.com/fwlink/?LinkID=132293) (http://go.Microsoft.com/fwlink/?) LinkID = 132293) espace de noms inclut la [Microsoft.VisualStudio.TestTools.UnitTesting.TestContext](http://go.microsoft.com/fwlink/?LinkID=208233) (http://go.Microsoft.com/fwlink/?) LinkID = 208233) classe pour stocker les informations fournies pour les tests unitaires et la [Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute](http://go.microsoft.com/fwlink/?LinkID=208235) (http://go.Microsoft.com/fwlink/?) LinkID = 208235) classe est utilisée pour définir des méthodes de Test. Pour des raisons de BizTalk Server de test de charge, les méthodes de Test doivent indiquer le message doit être chargé et le point de terminaison/URL à laquelle le message doit être envoyé. L’URL de point de terminaison/servira ensuite en tant que point d’entrée de message dans BizTalk Server lors de l’emplacement de réception BizTalk correspondant est créé.  
  
 À des fins d’illustration, l’exemple de code dans cette rubrique décrit les méthodes de Test qui utilisent la [System.ServiceModel.ChannelFactory(TChannel)](http://go.microsoft.com/fwlink/?LinkId=208238) (http://go.Microsoft.com/fwlink/?) LinkID = 208238) pour envoyer des messages aux points de terminaison de service qui utilisent le point de terminaison WCF net.tcp et qui sont surveillés par BizTalk WCF-Custom classe d’adaptateur de réception. Points de terminaison de service pour les messages de test sont définis dans le fichier de Configuration de l’Application (app.config) du projet de Test.  
  
 Pour plus d’informations sur les Tests unitaires Visual Studio, consultez [Anatomie d’un Test unitaire](http://go.microsoft.com/fwlink/?LinkID=208232) (http://go.microsoft.com/fwlink/?LinkID=208232).  
  
 Suivez les étapes décrites dans les sections ci-dessous pour créer un projet de Test avec un Test unitaire pour soumettre des documents à un ou plusieurs ordinateurs BizTalk Server. Ces étapes ont été effectués à l’aide de Visual Studio 2010 Ultimate édition.  
  
### <a name="set-visual-studio-2010-test-project-options"></a>Définir les Options de projet de Test Visual Studio 2010  
  
1.  Lancez Visual Studio 2010 Ultimate édition. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Visual Studio 2010** puis cliquez sur **Microsoft Visual Studio 2010**.  
  
2.  Dans Visual Studio 2010, cliquez sur **outils** puis cliquez sur **Options** pour afficher les **Options** boîte de dialogue.  
  
3.  Cliquez pour développer **outils de Test** puis cliquez sur **un projet de Test** pour afficher les options pour la création de nouveaux projets de test.  
  
4.  Définir le **langage de projet de test par défaut :** à **le projet de test Visual c#**.  
  
5.  Sous l’option à **sélectionner les fichiers qui seront ajoutés à chaque nouveau projet de test par défaut :** sélectionnez **le projet de test Visual c#**et désactivez tous les types de test pour Visual c# de projets à l’exception des detest **Test unitaire**.  
  
6.  Cliquez sur **OK** pour fermer la boîte de dialogue **Options** .  
  
### <a name="create-a-new-visual-studio-2010-solution-with-a-test-project"></a>Créer une nouvelle Solution Visual Studio 2010 avec un projet de Test  
  
1.  Créez le dossier **C:\Projects** sur l’ordinateur Visual Studio 2010 Ultimate.  
  
2.  Dans Visual Studio 2010, cliquez sur **fichier**, pointez sur **nouveau**, puis cliquez sur **projet** pour afficher les **nouveau projet** boîte de dialogue.  
  
3.  Sous **modèles installés** cliquez pour développer **Visual C#**, puis cliquez sur **Test**.  
  
4.  Au bas de la **nouveau projet** boîte de dialogue spécifier les options suivantes :  
  
    -   **Nom :**  
         **BTSLoad**  
  
    -   **Emplacement :**  
         **C:\projects\\**  
  
    -   **Nom de la solution :**  
         **Test de charge**  
  
5.  Assurez-vous que l’option à **créer le répertoire pour la solution** est activée, puis cliquez sur **OK**.  
  
6.  Ajouter un dossier dans le projet BTSLoad ; ce dossier contient les messages de test à être soumis à BizTalk Server. Dans l’Explorateur de solutions, cliquez sur le projet BTSLoad, pointez sur **ajouter**, puis cliquez sur **nouveau dossier**. Une icône de dossier avec le texte mis en surbrillance **Nouveaudossier1** s’affiche sous le projet BTSLoad, type **TestMessages** pour modifier le texte mis en surbrillance et appuyez sur la **entrée** clé Pour créer le dossier C:\Projects\LoadTest\BTSLoad\TestMessages.  
  
### <a name="update-the-code-in-the-test-project-and-add-an-application-configuration-file-to-the-test-project"></a>Mettre à jour le Code dans le projet de Test et ajouter un fichier de Configuration d’Application au projet de Test  
  
1.  Dans l’Explorateur de solutions sélectionnez **UnitTest1.cs** et remplacez le code existant par l’exemple de liste de code suivante :  
  
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
  
2.  Ajoutez un fichier de Configuration de l’Application au projet de Test :  
  
    1.  Dans l’Explorateur de solutions, cliquez sur le projet BTSLoad, pointez sur **ajouter** et cliquez sur **un nouvel élément**.  
  
    2.  Dans le **ajouter un nouvel élément** boîte de dialogue **modèles installés**, cliquez sur **général**.  
  
    3.  Dans la liste des éléments qui sont affichés sélectionnez **fichier de Configuration d’Application** puis cliquez sur **ajouter**.  
  
    4.  Dans l’Explorateur de solutions, sélectionnez le fichier app.config et remplacez le contenu du fichier app.config avec l’exemple de code sous :  
  
        > [!IMPORTANT]  
        >  Pour chaque point de terminaison client défini dans ce fichier, *ordinateur BizTalk Server* est un espace réservé pour le nom réel de l’ou les ordinateurs que vous effectuerez chargement de test par rapport à BizTalk Server.  
  
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
  
    5.  Cliquez sur le **fichier** menu dans Visual Studio 2010, puis cliquez sur **Enregistrer tout**.  
  
### <a name="add-a-test-message-to-the-project"></a>Ajouter un Message de Test au projet  
 Pour des raisons de cet exemple, BizTalk Server emplacements de réception et envoi du port (s) est configuré pour utiliser passent par les pipelines et n’effectue aucune validation de document. Suivez ces étapes pour ajouter un message de test au projet :  
  
1.  Lancez le bloc-notes. Cliquez sur **Démarrer**, cliquez sur **exécuter** et type **bloc-notes** dans les **exécuter** boîte de dialogue.  
  
2.  Copiez le texte suivant dans le bloc-notes et l’enregistrer en tant que « C:\Projects\LoadTest\BTSLoad\TestMessages\TestXmlDocument.xml »  
  
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
  
3.  Fermez le Bloc-notes.  
  
> [!IMPORTANT]  
>  Ce fichier sera doivent être enregistrés pour le même chemin d’accès à l’aide du même nom sur chaque ordinateur Agent de Test de charge si plusieurs ordinateurs de l’Agent de Test de charge sont utilisés pour le test de charge.  
  
### <a name="add-necessary-references-to-the-project-and-build-the-test-project"></a>Ajouter les références nécessaires au projet et générez le projet de Test  
  
1.  Dans l’Explorateur de solutions, cliquez sur le **références** dossier pour le projet de BTSLoad, puis cliquez sur **ajouter une référence**.  
  
2.  Dans la boîte de dialogue Ajouter une référence, cliquez sur le **.NET** onglet et utiliser la combinaison de la souris et clavier CTRL + clic pour sélectionner simultanément des espaces de noms .NET suivants :  
  
    -   System.Configuration  
  
    -   System.Runtime.Serialization  
  
    -   System.ServiceModel.Channels  
  
    -   System.ServiceModel  
  
    -   System.Web.Extensions  
  
    -   System.Xml  
  
3.  Après avoir sélectionné les espaces de noms, cliquez sur **OK** pour ajouter ces assemblys en tant que références au projet de Test de BTSLoad.  
  
4.  Bouton droit sur le **BTSLoad** de projet, puis cliquez sur **générer** pour compiler le projet dans l’assembly BTSLoad.