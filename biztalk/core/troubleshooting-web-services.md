---
title: "Dépannage des Services Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c32bf542-dcc6-4727-b31f-52bb19d4b89d
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c41800d53005d9f0a8f1472cd61abcd873c84394
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-web-services"></a><span data-ttu-id="51938-102">Dépannage des Services Web</span><span class="sxs-lookup"><span data-stu-id="51938-102">Troubleshooting Web Services</span></span>
<span data-ttu-id="51938-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exploite pleinement les services Web dans le cadre de l'utilisation de l'adaptateur SOAP et lors de la publication d'orchestrations en tant que services Web.</span><span class="sxs-lookup"><span data-stu-id="51938-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes extensive use of Web services for use with the SOAP adapter and when publishing orchestrations as Web services.</span></span> <span data-ttu-id="51938-104">Cette rubrique propose des procédures à suivre pour résoudre les problèmes liés aux services Web que vous êtes le plus susceptible de rencontrer.</span><span class="sxs-lookup"><span data-stu-id="51938-104">This topic provides some steps that you can follow to troubleshoot Web services, as well as some common Web services problems and how to resolve those problems.</span></span>  
  
## <a name="use-net-framework-tracing-to-capture-and-log-errors-in-a-web-service"></a><span data-ttu-id="51938-105">Utilisation du suivi .NET Framework pour capturer et consigner les erreurs d'un service Web</span><span class="sxs-lookup"><span data-stu-id="51938-105">Use .NET Framework tracing to capture and log errors in a Web service</span></span>  
 <span data-ttu-id="51938-106">Le .NET Framework **System.Diagnostics.Trace** classe peut être utilisée pour capturer et écrire les erreurs dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="51938-106">The .NET Framework **System.Diagnostics.Trace** class can be used to capture and write errors to a text file.</span></span>  
  
#### <a name="to-use-the-systemdiagnosticstrace-class-to-capture-and-write-errors-to-a-text-file"></a><span data-ttu-id="51938-107">Utilisation de la classe System.Diagnostics.Trace pour capturer et écrire les erreurs dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="51938-107">To use the System.Diagnostics.Trace class to capture and write errors to a text file</span></span>  
  
1.  <span data-ttu-id="51938-108">Mettre à jour le fichier web.config pour le service Web définir le **TRACE** directive de compilateur pour **true** et ajoutez un **TraceSwitch** valeur :</span><span class="sxs-lookup"><span data-stu-id="51938-108">Update the web.config file for the Web service to set the **TRACE** compiler directive to **true** and add a **TraceSwitch** value:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <configuration>  
      <system.codedom>  
        <compilers>  
          <compiler language="c#;cs;csharp"   
                    extension=".cs"   
                    compilerOptions="/d:TRACE"  
                    type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.3500.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" warningLevel="1" />  
          </compilers>  
      </system.codedom>  
      <system.diagnostics>  
        <switches>  
          <add name="WebSvcTraceSwitch" value="2" />  
          <!-- Set to 0, 1, 2, 3, or 4, which corresponds   
          to TraceLevel.Off, TraceLevel.Error, TraceLevel.Warning  
          TraceLevel.Info, and TraceLevel.Verbose. -->  
        </switches>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="51938-109">Si le **TRACE** directive de compilateur n’est pas définie sur **true** , aucune sortie de trace ne sera généré.</span><span class="sxs-lookup"><span data-stu-id="51938-109">If the **TRACE** compiler directive is not set to **true** then no trace output will be generated.</span></span> <span data-ttu-id="51938-110">Le **TraceSwitch** valeur peut également être définie dans l’appel de la classe, mais est définie ici dans le fichier web.config pour des raisons pratiques.</span><span class="sxs-lookup"><span data-stu-id="51938-110">The **TraceSwitch** value can also be set in the calling class, but is set here in the web.config file for convenience.</span></span> <span data-ttu-id="51938-111">Définir le **TraceSwitch** valeur au niveau approprié pour le développement et modifiez la valeur issue du développement afin de réduire ou désactiver la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="51938-111">Set the **TraceSwitch** value to the appropriate level for development purposes and change the value after development is complete to reduce or inhibit trace output.</span></span>  
  
2.  <span data-ttu-id="51938-112">Créez une instance de la **TraceSwitch** et **TextWriterTraceListener** classes et utiliser un **try... catch** bloquer dans l’appel de service [WebMethod] Web pour intercepter et écrire les erreurs dans un fichier de sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="51938-112">Create an instance of the **TraceSwitch** and **TextWriterTraceListener** classes and use a **try…catch** block in the Web service [WebMethod] call to trap and write errors to a trace output file.</span></span> <span data-ttu-id="51938-113">Par exemple, le code suivant intercepte une erreur qui est générée lors de la tentative de définition de la variable entière s2 sur une instance null de la variable objet o2 :</span><span class="sxs-lookup"><span data-stu-id="51938-113">For example, the following code traps an error that is generated when attempting to set the integer variable s2 to a null instance of the object variable o2:</span></span>  
  
    ```  
    using System;  
    using System.Web;  
    using System.Web.Services;  
    using System.Web.Services.Protocols;  
    using System.Diagnostics;  
  
    [WebService(Namespace = "http://tempuri.org/")]  
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
    public class Service : System.Web.Services.WebService  
    {  
        TraceSwitch WebSvcTraceSwitch = new TraceSwitch("WebSvcTraceSwitch", "Web Service Trace");  
        TextWriterTraceListener TestTracer = new TextWriterTraceListener("C:\\traceout.txt");  
        // Note that by default the local ASPNET account(IIS 5.x) or the   
        // local NETWORK SERVICE account(IIS 6.0) needs write access to  
        // this directory so that the instance of the   
        // TextWriterTraceListener can write to the trace output file.  
    );  
  
        public Service () {  
        }  
  
        [WebMethod]  
        public string HelloWorld()   
        {  
        string h2 = "Hello World";  
        //object o2 = 1;  
        object o2 = null;  
            try  
            {  
                int s2 = (int)o2; //Error if o2 set to null   
                return h2;  
            }  
            catch(Exception e)  
            {  
                Trace.Listeners.Add(TestTracer);  
                Trace.WriteLineIf(WebSvcTraceSwitch.Level = TraceLevel.Warning, "Exception caught: " + e.Message);  
                //Writes to the trace file if specified TraceLevel switch value (in web.config) >= 2  
                TestTracer.Dispose();  
                return "An error occurred in the Web service, please contact the web server administrator.";  
            }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="51938-114">Ce code est une version modifiée de la valeur par défaut du service HelloWorld Web qui est généré lorsque vous créez un nouveau **Service Web ASP.Net** projet dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51938-114">This code is a modified version of the default HelloWorld Web service that is generated when you create a new **ASP.Net Web Service** project in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="51938-115">Pour Windows Vista, des privilèges d’administrateur peuvent être nécessaires pour écrire le fichier de sortie de trace dans le dossier racine.</span><span class="sxs-lookup"><span data-stu-id="51938-115">For Windows Vista, Administrator privileges may be required to write the trace output file to the root folder.</span></span>  
  
3.  <span data-ttu-id="51938-116">Reconstruisez le projet de service Web.</span><span class="sxs-lookup"><span data-stu-id="51938-116">Rebuild the Web service project.</span></span> <span data-ttu-id="51938-117">Maintenant, si une erreur se produit dans le **essayez** instruction l’exception est gérée dans le **Catch** instruction et une erreur est écrite dans le fichier de sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="51938-117">Now, if an error occurs in the **Try** statement the exception is handled in the **Catch** statement and an error is written to the trace output file.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="51938-118">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="51938-118">Known Issues</span></span>  
  
#### <a name="a-web-service-returns-an-http-404-file-not-found-error"></a><span data-ttu-id="51938-119">Un service Web retourne une erreur HTTP 404 (fichier introuvable).</span><span class="sxs-lookup"><span data-stu-id="51938-119">A Web service returns an HTTP 404 (File Not Found) error</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="51938-120">Problème</span><span class="sxs-lookup"><span data-stu-id="51938-120">Problem</span></span>  
 <span data-ttu-id="51938-121">Les tentatives d'appel d'un service Web renvoient une erreur HTTP 404 (fichier introuvable).</span><span class="sxs-lookup"><span data-stu-id="51938-121">Attempts to call a Web service return an HTTP 404 (File Not Found) error.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="51938-122">Cause</span><span class="sxs-lookup"><span data-stu-id="51938-122">Cause</span></span>  
 <span data-ttu-id="51938-123">Cette erreur peut se produire si ASP.NET n'est pas installé et/ou activé sur le serveur IIS qui héberge le service Web.</span><span class="sxs-lookup"><span data-stu-id="51938-123">This error can occur if ASP.NET is not installed and/or enabled on the IIS server that hosts the Web service.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="51938-124">Résolution</span><span class="sxs-lookup"><span data-stu-id="51938-124">Resolution</span></span>  
 <span data-ttu-id="51938-125">Assurez-vous qu'ASP.NET est installé et activé.</span><span class="sxs-lookup"><span data-stu-id="51938-125">Ensure that ASP.NET is installed and enabled.</span></span> <span data-ttu-id="51938-126">Installer le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] si elle n’est pas installé et/ou exécutez le **aspnet_regiis.exe** programme situé dans le %WinDir%\Microsoft.NET\Framework\\*vXXX.XXX*\ dossier du serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="51938-126">Install the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] if it is not installed and/or run the **aspnet_regiis.exe** program located in the %WinDir%\Microsoft.NET\Framework\\*vXXX.XXX*\ folder of the IIS server.</span></span>  
  
#### <a name="a-systemiofilenotfoundexception-error-occurs-when-a-web-service-is-called"></a><span data-ttu-id="51938-127">Une erreur « System.IO.FileNotFoundException » se produit lorsqu'un service Web est appelé.</span><span class="sxs-lookup"><span data-stu-id="51938-127">A "System.IO.FileNotFoundException" error occurs when a Web service is called</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="51938-128">Problème</span><span class="sxs-lookup"><span data-stu-id="51938-128">Problem</span></span>  
 <span data-ttu-id="51938-129">Lorsque vous appelez un service Web dans une application Web Microsoft ASP.NET, il est possible que vous receviez l'erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="51938-129">When you call a Web service in a Microsoft ASP.NET Web application, you may receive the following error:</span></span>  
  
 <span data-ttu-id="51938-130">**System.IO.FileNotFoundException**</span><span class="sxs-lookup"><span data-stu-id="51938-130">**System.IO.FileNotFoundException**</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="51938-131">Cause</span><span class="sxs-lookup"><span data-stu-id="51938-131">Cause</span></span>  
 <span data-ttu-id="51938-132">Cette erreur peut se produire si l'une des conditions suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="51938-132">This error can occur if either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="51938-133">Le processus de travail ne dispose ni des autorisations pour lire le répertoire temporaire de processus ni des autorisations pour écrire dans le répertoire temporaire de processus.</span><span class="sxs-lookup"><span data-stu-id="51938-133">The worker process does not have permissions to read to the process Temp directory, and the worker process does not have permissions to write to the process Temp directory.</span></span>  
  
-   <span data-ttu-id="51938-134">Le code généré par XmlSerializer contient des erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="51938-134">There are compilation errors in the code that XmlSerializer generated.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="51938-135">Résolution</span><span class="sxs-lookup"><span data-stu-id="51938-135">Resolution</span></span>  
 <span data-ttu-id="51938-136">Cette erreur est documentée dans la Base de connaissances Microsoft l’article 823196, [PRB : vous recevez un « System.IO.FileNotFoundException » erreur lorsque le Client Application appelle un Service Web](http://go.microsoft.com/fwlink/?LinkID=84694)».</span><span class="sxs-lookup"><span data-stu-id="51938-136">This error is documented in Microsoft Knowledge Base article 823196, [PRB: You Receive a "System.IO.FileNotFoundException" Error When the Client Application Calls a Web Service](http://go.microsoft.com/fwlink/?LinkID=84694)".</span></span> <span data-ttu-id="51938-137">Suivez les étapes de la section Résolution de cet article pour corriger cette erreur.</span><span class="sxs-lookup"><span data-stu-id="51938-137">Follow the steps in the Resolution section of this Knowledge Base article to resolve this error.</span></span>  
  
#### <a name="date-fields-are-removed-from-documents-processed-by-a-web-service-generated-with-the-biztalk-server-web-services-publishing-wizard"></a><span data-ttu-id="51938-138">Les champs de date sont supprimés des documents traités par un service Web généré avec l'Assistant Publication de services Web de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="51938-138">Date fields are removed from documents processed by a web service generated with the BizTalk Server Web Services Publishing Wizard</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="51938-139">Problème</span><span class="sxs-lookup"><span data-stu-id="51938-139">Problem</span></span>  
 <span data-ttu-id="51938-140">Lorsque vous traitez un document avec un service web qui a été généré avec le BizTalk Server Web Assistant Publication de Services, les données contenues dans un champ avec un **Type de données** de **xs : date** et un  **Nillable** propriété du **True** est supprimé du document.</span><span class="sxs-lookup"><span data-stu-id="51938-140">When you process a document with a web service that was generated with the BizTalk Server Web Services Publishing Wizard, any data contained in a field with a **Data Type** of **xs:date** and a **Nillable** property of **True** is removed from the document.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="51938-141">Cause</span><span class="sxs-lookup"><span data-stu-id="51938-141">Cause</span></span>  
 <span data-ttu-id="51938-142">Ce problème est lié à un problème connu relatif à la classe XmlSerializer, qui est disponible avec l'espace de noms de la Bibliothèque de classes Microsoft .NET Framework System.Xml.Serialization.</span><span class="sxs-lookup"><span data-stu-id="51938-142">This problem occurs because of a known issue with the XmlSerializer class that is available with the Microsoft .NET Framework Class Library namespace System.Xml.Serialization.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="51938-143">Résolution</span><span class="sxs-lookup"><span data-stu-id="51938-143">Resolution</span></span>  
 <span data-ttu-id="51938-144">Pour résoudre ce problème, installez le correctif .NET Framework 2.0 documenté dans la Base de connaissances Microsoft l’article 925272, «[FIX : sérialisation XML le risque de perdre certains éléments facultatifs dans un schéma XSD dans le .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkId=84696)».</span><span class="sxs-lookup"><span data-stu-id="51938-144">To resolve this issue, install the .NET Framework 2.0 hotfix documented in Microsoft Knowledge Base article 925272, "[FIX: The XML serialization may lose some optional elements in an XSD schema in the .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkId=84696)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51938-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51938-145">See Also</span></span>  
 <span data-ttu-id="51938-146">[Instructions pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md) </span><span class="sxs-lookup"><span data-stu-id="51938-146">[Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) </span></span>  
 [<span data-ttu-id="51938-147">Instructions pour la résolution des problèmes d’autorisations Web Services</span><span class="sxs-lookup"><span data-stu-id="51938-147">Guidelines for Resolving Web Services Permissions Problems</span></span>](../core/guidelines-for-resolving-web-services-permissions-problems.md)