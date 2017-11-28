---
title: "Dépannage des Services Web BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdc86de8-e41e-4878-a66e-e242bcf3b705
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 666b08e0c7992f8660d005bef51d26c8f51bbed5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-web-services"></a><span data-ttu-id="05203-102">Dépannage des services Web BizTalk</span><span class="sxs-lookup"><span data-stu-id="05203-102">Troubleshooting BizTalk Web Services</span></span>
<span data-ttu-id="05203-103">Cette section explique comment identifier et résoudre les problèmes courants relatifs aux services Web.</span><span class="sxs-lookup"><span data-stu-id="05203-103">This section offers advice on how to identify and resolve common Web service issues.</span></span>  
  
## <a name="general-troubleshooting"></a><span data-ttu-id="05203-104">Dépannage d'ordre général</span><span class="sxs-lookup"><span data-stu-id="05203-104">General Troubleshooting</span></span>  
  
### <a name="enabling-web-services-publishing-wizard-tracing"></a><span data-ttu-id="05203-105">Activation du suivi de l'Assistant Publication de services Web</span><span class="sxs-lookup"><span data-stu-id="05203-105">Enabling Web Services Publishing Wizard tracing</span></span>  
 <span data-ttu-id="05203-106">Vous pouvez activer le suivi pour déboguer l’Assistant de publication des Services Web BizTalk en supprimant commentaires le \<Ajouter > nœud dans le fichier BTSWebSvcWiz.exe.config.</span><span class="sxs-lookup"><span data-stu-id="05203-106">You can enable tracing to debug the BizTalk Web Services Publishing Wizard by uncommenting the \<add> node in the BTSWebSvcWiz.exe.config file.</span></span> <span data-ttu-id="05203-107">Pour plus d’informations sur l’obtention des informations de trace à partir de l’Assistant Publication de Services Web, consultez [comment modifier les BTSWebSvcWiz.exe.config](../core/how-to-modify-btswebsvcwiz-exe-config.md).</span><span class="sxs-lookup"><span data-stu-id="05203-107">For more information about obtaining trace information from the Web Services Publishing Wizard, see [How to Modify BTSWebSvcWiz.exe.config](../core/how-to-modify-btswebsvcwiz-exe-config.md).</span></span>  
  
### <a name="enabling-soap-message-tracing"></a><span data-ttu-id="05203-108">Activation du suivi de message SOAP</span><span class="sxs-lookup"><span data-stu-id="05203-108">Enabling SOAP message tracing</span></span>  
 <span data-ttu-id="05203-109">Vous pouvez activer le suivi de message SOAP pour déboguer l'application de publication de services Web à l'aide d'une extension SOAP.</span><span class="sxs-lookup"><span data-stu-id="05203-109">You can enable SOAP message tracing to help you debug the Web services publishing application by using a SOAP extension.</span></span> <span data-ttu-id="05203-110">Pour plus d’informations sur les extensions SOAP, consultez [Comment : implémenter une Extension SOAP](http://go.microsoft.com/fwlink/?LinkId=62314).</span><span class="sxs-lookup"><span data-stu-id="05203-110">For more information about SOAP extensions, see [How to: Implement a SOAP Extension](http://go.microsoft.com/fwlink/?LinkId=62314).</span></span>  
  
### <a name="using-the-throwdetailederror-switch"></a><span data-ttu-id="05203-111">Utilisation du commutateur ThrowDetailedError</span><span class="sxs-lookup"><span data-stu-id="05203-111">Using the ThrowDetailedError switch</span></span>  
 <span data-ttu-id="05203-112">Si une erreur se produit, le client Web reçoit un générique **SoapException**.</span><span class="sxs-lookup"><span data-stu-id="05203-112">If an error occurs, the Web client receives a generic **SoapException**.</span></span>  
  
 <span data-ttu-id="05203-113">Pour déboguer votre service Web publié, vous pouvez ajouter un commutateur au fichier web.config pour contrôler le niveau de détails de l’exception retournée par le service Web publié.</span><span class="sxs-lookup"><span data-stu-id="05203-113">To debug your published Web service, you can add a switch to the web.config file to control the level of the exception details returned from the published Web service.</span></span> <span data-ttu-id="05203-114">Le commutateur est **ThrowDetailedError**, et si elle est définie **True** le serveur proxy retourne des informations sur l’exception interne au client Web, ce qui vous permet de déboguer le service Web publié.</span><span class="sxs-lookup"><span data-stu-id="05203-114">The switch is **ThrowDetailedError**, and when it is set to **True** the server proxy returns inner exception information to the Web client, enabling you to debug the published Web service.</span></span>  
  
 <span data-ttu-id="05203-115">Le code XML suivant montre la **ThrowDetailedError** commutateur qui apparaît dans le fichier web.config sous le \<appSettings > nœud :</span><span class="sxs-lookup"><span data-stu-id="05203-115">The following XML code shows the **ThrowDetailedError** switch that appears in the web.config file under the \<appSettings> node:</span></span>  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!WARNING]
>  <span data-ttu-id="05203-116">L'exception interne peut contenir des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="05203-116">The inner exception may contain sensitive information.</span></span> <span data-ttu-id="05203-117">Après le débogage, vous devez définir le **ThrowDetailedError** basculer vers **False**.</span><span class="sxs-lookup"><span data-stu-id="05203-117">After debugging, you should set the **ThrowDetailedError** switch to **False**.</span></span>  
  
### <a name="using-net-framework-tracing-to-capture-and-log-errors-in-the-web-service"></a><span data-ttu-id="05203-118">Utilisation du suivi .NET Framework pour capturer et consigner les erreurs du service Web</span><span class="sxs-lookup"><span data-stu-id="05203-118">Using .NET Framework tracing to capture and log errors in the Web service</span></span>  
 <span data-ttu-id="05203-119">Le .NET Framework **System.Diagnostics.Trace** classe peut être utilisée pour capturer et écrire les erreurs dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="05203-119">The .NET Framework **System.Diagnostics.Trace** class can be used to capture and write errors to a text file.</span></span>  
  
##### <a name="to-use-the-systemdiagnosticstrace-class-to-capture-and-write-errors-to-a-text-file"></a><span data-ttu-id="05203-120">Utilisation de la classe System.Diagnostics.Trace pour capturer et écrire les erreurs dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="05203-120">To use the System.Diagnostics.Trace class to capture and write errors to a text file</span></span>  
  
1.  <span data-ttu-id="05203-121">Mettre à jour le fichier web.config pour le service Web définir la directive de compilateur TRACE sur **true** et ajoutez un **TraceSwitch** valeur :</span><span class="sxs-lookup"><span data-stu-id="05203-121">Update the web.config file for the Web service to set the TRACE compiler directive to **true** and add a **TraceSwitch** value:</span></span>  
  
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
    >  <span data-ttu-id="05203-122">Si la directive de compilateur TRACE n’est pas définie sur **true** , aucune sortie de trace ne sera généré.</span><span class="sxs-lookup"><span data-stu-id="05203-122">If the TRACE compiler directive is not set to **true** then no trace output will be generated.</span></span> <span data-ttu-id="05203-123">Le **TraceSwitch** valeur peut également être définie dans la classe appelante mais est définie ici dans le fichier web.config pour des raisons pratiques.</span><span class="sxs-lookup"><span data-stu-id="05203-123">The **TraceSwitch** value can also be set in the calling class but is set here in the web.config file for convenience.</span></span> <span data-ttu-id="05203-124">Définir le **TraceSwitch** valeur au niveau approprié pour le développement et modifiez la valeur issue du développement afin de réduire ou désactiver la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="05203-124">Set the **TraceSwitch** value to the appropriate level for development purposes and change the value after development is complete to reduce or inhibit trace output.</span></span>  
  
2.  <span data-ttu-id="05203-125">Créez une instance de la **TraceSwitch** et **TextWriterTraceListener** classes et utiliser un **try... catch** bloquer dans l’appel de service [WebMethod] Web pour intercepter et écrire les erreurs dans un fichier de sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="05203-125">Create an instance of the **TraceSwitch** and **TextWriterTraceListener** classes and use a **try…catch** block in the Web service [WebMethod] call to trap and write errors to a trace output file.</span></span> <span data-ttu-id="05203-126">Par exemple, le code suivant intercepte une erreur qui est générée lors de la tentative de définition de la variable entière s2 sur une instance null de la variable objet o2 :</span><span class="sxs-lookup"><span data-stu-id="05203-126">For example, the following code traps an error that is generated when attempting to set the integer variable s2 to a null instance of the object variable o2:</span></span>  
  
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
                Trace.WriteLineIf(WebSvcTraceSwitch.Level = TraceLevel.Warning,"Exception caught: " + e.Message);  
                //Writes to the trace file if specified TraceLevel switch value (in web.config) >= 2  
                TestTracer.Dispose();  
                return "An error occurred in the Web service, please contact the web server administrator.";  
            }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="05203-127">Ce code est une version modifiée du service HelloWorld Web qui est généré par défaut lorsque vous créez un nouveau **Service Web ASP.Net** projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05203-127">This code is a modified version of the HelloWorld Web service that is generated by default when you create a new **ASP.Net Web Service** project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="05203-128">Pour Windows Vista, des privilèges d’administrateur peuvent être nécessaires pour écrire le fichier de sortie de trace dans le dossier racine.</span><span class="sxs-lookup"><span data-stu-id="05203-128">For Windows Vista, Administrator privileges may be required to write the trace output file to the root folder.</span></span>  
  
3.  <span data-ttu-id="05203-129">Reconstruisez le projet de service Web.</span><span class="sxs-lookup"><span data-stu-id="05203-129">Rebuild the Web service project.</span></span> <span data-ttu-id="05203-130">Maintenant, si une erreur se produit dans le **essayez** instruction l’exception est gérée dans le **Catch** instruction et une erreur est écrite dans le fichier de sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="05203-130">Now, if an error occurs in the **Try** statement the exception is handled in the **Catch** statement and an error is written to the trace output file.</span></span>  
  
## <a name="general-troubleshooting-questions-and-answers"></a><span data-ttu-id="05203-131">Questions et réponses d'ordre général sur le dépannage</span><span class="sxs-lookup"><span data-stu-id="05203-131">General Troubleshooting Questions and Answers</span></span>  
 <span data-ttu-id="05203-132">Cette section présente un certain nombre de questions et réponses conçues pour vous aider à résoudre les problèmes liés aux services Web.</span><span class="sxs-lookup"><span data-stu-id="05203-132">This section contains a set of questions and answers designed to help you resolve issues with Web services.</span></span>  
  
### <a name="i-am-receiving-errors-when-consuming-a-web-service-how-can-i-avoid-them"></a><span data-ttu-id="05203-133">Je reçois des erreurs lorsque j'utilise un service Web. Comment puis-je y remédier ?</span><span class="sxs-lookup"><span data-stu-id="05203-133">I am receiving errors when consuming a Web service; how can I avoid them?</span></span>  
 <span data-ttu-id="05203-134">Vous devez tenir compte de nombreux détails lorsque vous utilisez un service Web, notamment les suivants :</span><span class="sxs-lookup"><span data-stu-id="05203-134">There are many details to consider when consuming a Web service, including the following:</span></span>  
  
-   <span data-ttu-id="05203-135">Évitez d'utiliser deux caractères de soulignement dans un nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="05203-135">Avoid using two underscore characters in a parameter name.</span></span>  
  
-   <span data-ttu-id="05203-136">Utilisation de la **tout** élément ou le **anyAttribute** attribut n’est pas pris en charge dans les méthodes Web.</span><span class="sxs-lookup"><span data-stu-id="05203-136">Use of the **any** element or the **anyAttribute** attribute is not supported in Web methods.</span></span>  
  
-   <span data-ttu-id="05203-137">Évitez d'utiliser des mots clés XLANG/s comme nom de service ou de méthode Web.</span><span class="sxs-lookup"><span data-stu-id="05203-137">Avoid using XLANG/s keywords as a Web service name or Web method name.</span></span>  
  
-   <span data-ttu-id="05203-138">Évitez d'utiliser des types de paramètre de méthode Web non pris en charge par XLANG/s.</span><span class="sxs-lookup"><span data-stu-id="05203-138">Avoid using Web method parameter types that are not supported by XLANG/s.</span></span>  
  
-   <span data-ttu-id="05203-139">N'utilisez pas de noms d'élément qui sont des mots clés C# ou qui ne sont pas valides en tant qu'identificateur C# dans vos schémas.</span><span class="sxs-lookup"><span data-stu-id="05203-139">Do not use element names that are C# keywords or will be invalid as a C# identifier in your schemas.</span></span>  
  
-   <span data-ttu-id="05203-140">Évitez les fichiers WSDL (Web Services Description Language) avec plusieurs définitions de service ou de type de port.</span><span class="sxs-lookup"><span data-stu-id="05203-140">Avoid Web Services Description Language (WSDL) files with multiple service or port type definitions.</span></span>  
  
-   <span data-ttu-id="05203-141">Paramètres de méthode Web doivent être sérialisables Xml.</span><span class="sxs-lookup"><span data-stu-id="05203-141">Web method parameters must be Xml Serializable.</span></span>  
  
-   <span data-ttu-id="05203-142">Évitez toute référence aux services Web utilisés contenant des schémas à plusieurs racines.</span><span class="sxs-lookup"><span data-stu-id="05203-142">Avoid references to consumed Web services that contain multi-rooted schemas.</span></span>  
  
-   <span data-ttu-id="05203-143">Évitez de référencer les services Web avec des méthodes Web qui attendent des paramètres basés sur des génériques, tels que des paramètres de type nullable.</span><span class="sxs-lookup"><span data-stu-id="05203-143">Avoid referencing Web services with Web methods expecting generic-based parameters such as nullable parameters.</span></span>  
  
-   <span data-ttu-id="05203-144">L'élément d'importation WSDL n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="05203-144">The WSDL import element is not supported.</span></span>  
  
 <span data-ttu-id="05203-145">Pour plus d’informations sur ces éléments et autres considérations connexes, consultez [Considérations lors de la consommation des Services Web](../core/considerations-when-consuming-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="05203-145">For more information about these and related considerations, see [Considerations When Consuming Web Services](../core/considerations-when-consuming-web-services.md).</span></span>  
  
### <a name="why-am-i-getting-errors-publishing-my-schema-that-uses-the-include-element"></a><span data-ttu-id="05203-146">Pourquoi les erreurs de publication mon schéma qui utilise le \<inclure > élément ?</span><span class="sxs-lookup"><span data-stu-id="05203-146">Why am I getting errors publishing my schema that uses the \<include> element?</span></span>  
 <span data-ttu-id="05203-147">Schémas ne peut pas être publiées si elles comprennent les références circulaires (le schéma inclus a un **incluent** élément vers le schéma, y compris) ou avoir un non résolue **schemaLocation** attribut.</span><span class="sxs-lookup"><span data-stu-id="05203-147">Schemas cannot be published if they include circular references (the included schema has an **include** element to the including schema) or have an unresolved **schemaLocation** attribute.</span></span>  
  
 <span data-ttu-id="05203-148">Pour plus d’informations sur la limitation de la **incluent** élément, consultez [Include Element Binding Support](http://go.microsoft.com/fwlink/?LinkId=62312).</span><span class="sxs-lookup"><span data-stu-id="05203-148">For more information about the limitation of the **include** element, see [Include Element Binding Support](http://go.microsoft.com/fwlink/?LinkId=62312).</span></span> <span data-ttu-id="05203-149">L’Assistant Publication de Services Web a les mêmes limitations que XSD.exe dans .NET Framework 2.0 ; Pour plus d’informations, consultez [Import Element Binding Support](http://go.microsoft.com/fwlink/?LinkId=119606).</span><span class="sxs-lookup"><span data-stu-id="05203-149">The Web Services Publishing Wizard has the same limitations as XSD.exe in .NET Framework 2.0; for more information, see [Import Element Binding Support](http://go.microsoft.com/fwlink/?LinkId=119606).</span></span>  
  
### <a name="why-do-i-receive-errors-when-publishing-my-envelope-schema"></a><span data-ttu-id="05203-150">Je reçois des erreurs lors de la publication de mon schéma d'enveloppe. Pourquoi ?</span><span class="sxs-lookup"><span data-stu-id="05203-150">Why do I receive errors when publishing my envelope schema?</span></span>  
 <span data-ttu-id="05203-151">Si vous publiez un schéma d'enveloppe en tant que service Web, vous devez modifier manuellement le projet Web généré.</span><span class="sxs-lookup"><span data-stu-id="05203-151">If you have an envelope schema that you are publishing as a Web service, you need to manually modify the generated Web project.</span></span>  
  
##### <a name="to-modify-the-generated-web-project-for-envelope-schemas"></a><span data-ttu-id="05203-152">Pour modifier le projet Web généré pour les schémas d'enveloppe</span><span class="sxs-lookup"><span data-stu-id="05203-152">To modify the generated Web project for envelope schemas</span></span>  
  
1.  <span data-ttu-id="05203-153">Ouvrez le  *\<myWebService >*. asmx.cs fichier.</span><span class="sxs-lookup"><span data-stu-id="05203-153">Open the *\<myWebService>*.asmx.cs file.</span></span>  
  
2.  <span data-ttu-id="05203-154">Éditez le fichier et changez la valeur de `bodyTypeAssemblyQualifiedName = <dll.name.version>` en `bodyTypeAssemblyQualifiedName = null`</span><span class="sxs-lookup"><span data-stu-id="05203-154">Edit the file and change `bodyTypeAssemblyQualifiedName = <dll.name.version>` to `bodyTypeAssemblyQualifiedName = null`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05203-155">Il peut être nécessaire de réinitialiser les services Internet (IIS) si le précédent fichier .dll est toujours présent dans le processus de travail ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="05203-155">You may need to reset Internet Information Services (IIS) if the previous .dll file is still in the ASP.NET worker process.</span></span>  
  
### <a name="clients-of-published-web-services-may-not-receive-server-script-time-out-errors"></a><span data-ttu-id="05203-156">Les clients de services Web publiés peuvent ne pas recevoir d'erreurs d'expiration de script de serveur.</span><span class="sxs-lookup"><span data-stu-id="05203-156">Clients of published Web services may not receive server script time-out errors</span></span>  
 <span data-ttu-id="05203-157">Si des clients Web utilisant .NET Framework appellent un service Web généré avec l'Assistant Publication de services Web [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est possible que le client ne puisse pas recevoir d'erreurs d'expiration de script de serveur, l'expiration de la requête du client se produisant en premier par défaut.</span><span class="sxs-lookup"><span data-stu-id="05203-157">If Web clients that use .NET Framework are calling a Web service generated with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web Services Publishing Wizard, it is possible that the client cannot receive server script time-out errors because the client request time-out occurs first by default.</span></span> <span data-ttu-id="05203-158">Pour résoudre ce problème, vous pouvez effectuer une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="05203-158">To resolve this problem you can do one of the following:</span></span>  
  
-   <span data-ttu-id="05203-159">Augmenter le délai d’attente de demande client pour une valeur supérieure au délai d’expiration de script de serveur en augmentant la valeur de la **HttpWebRequest.Timeout** propriété sur le client.</span><span class="sxs-lookup"><span data-stu-id="05203-159">Increase the client request time-out to a value greater than the server script time-out by increasing the value for the **HttpWebRequest.Timeout** property on the client.</span></span>  
  
-   <span data-ttu-id="05203-160">Réduire le délai d’expiration de script de serveur à une valeur inférieure au délai d’attente de la demande client en réduisant la valeur pour le **HttpServerUtility.ScriptTimeout** propriété sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="05203-160">Reduce the server script time-out to a value less than the client request time-out by reducing the value for the **HttpServerUtility.ScriptTimeout** property on the server.</span></span>  
  
## <a name="common-errors"></a><span data-ttu-id="05203-161">Erreurs fréquentes</span><span class="sxs-lookup"><span data-stu-id="05203-161">Common Errors</span></span>  
  
### <a name="a-web-service-returns-an-http-404-file-not-found-error"></a><span data-ttu-id="05203-162">Un service Web retourne une erreur HTTP 404 (fichier introuvable).</span><span class="sxs-lookup"><span data-stu-id="05203-162">A Web service returns an HTTP 404 (File Not Found) error</span></span>  
  
#### <a name="problem"></a><span data-ttu-id="05203-163">Problème</span><span class="sxs-lookup"><span data-stu-id="05203-163">Problem</span></span>  
 <span data-ttu-id="05203-164">Les tentatives d'appel d'un service Web renvoient une erreur HTTP 404 (fichier introuvable).</span><span class="sxs-lookup"><span data-stu-id="05203-164">Attempts to call a Web service return an HTTP 404 (File Not Found) error.</span></span>  
  
#### <a name="cause"></a><span data-ttu-id="05203-165">Cause</span><span class="sxs-lookup"><span data-stu-id="05203-165">Cause</span></span>  
 <span data-ttu-id="05203-166">Cette erreur peut se produire si ASP.NET n'est pas installé et/ou activé sur le serveur IIS qui héberge le service Web.</span><span class="sxs-lookup"><span data-stu-id="05203-166">This error can occur if ASP.NET is not installed and/or enabled on the IIS server that hosts the Web service.</span></span>  
  
#### <a name="resolution"></a><span data-ttu-id="05203-167">Résolution</span><span class="sxs-lookup"><span data-stu-id="05203-167">Resolution</span></span>  
 <span data-ttu-id="05203-168">Assurez-vous qu'ASP.NET est installé et activé.</span><span class="sxs-lookup"><span data-stu-id="05203-168">Ensure that ASP.NET is installed and enabled.</span></span> <span data-ttu-id="05203-169">Installez .NET Framework s'il n'est pas déjà installé et/ou exécutez le programme aspnet_regiis.exe situé dans le dossier %WinDir%\Microsoft.NET\Framework\vXXX.XXX\ du serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="05203-169">Install the .NET Framework if it is not installed and/or run the aspnet_regiis.exe program located in the %WinDir%\Microsoft.NET\Framework\vXXX.XXX\ folder of the IIS server.</span></span>  
  
### <a name="date-fields-are-removed-from-documents-processed-by-a-web-service-generated-with-the-biztalk-server-web-services-publishing-wizard"></a><span data-ttu-id="05203-170">Les champs de date sont supprimés des documents traités par un service Web généré avec l'Assistant Publication de services Web de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="05203-170">Date fields are removed from documents processed by a web service generated with the BizTalk Server Web Services Publishing Wizard</span></span>  
  
#### <a name="problem"></a><span data-ttu-id="05203-171">Problème</span><span class="sxs-lookup"><span data-stu-id="05203-171">Problem</span></span>  
 <span data-ttu-id="05203-172">Lorsque vous traitez un document avec un service web qui a été généré avec le BizTalk Server Web Assistant Publication de Services, les données contenues dans un champ avec un **Type de données** de **xs : date** est supprimé de la document.</span><span class="sxs-lookup"><span data-stu-id="05203-172">When you process a document with a web service that was generated with the BizTalk Server Web Services Publishing Wizard, any data contained in a field with a **Data Type** of **xs:date** is removed from the document.</span></span>  
  
#### <a name="cause"></a><span data-ttu-id="05203-173">Cause</span><span class="sxs-lookup"><span data-stu-id="05203-173">Cause</span></span>  
 <span data-ttu-id="05203-174">Ce problème peut se produire si l’orchestration publiée contient un schéma avec un ou plusieurs champs qui ont un **Type de données** de **xs : date** et un **Nillable** propriété de  **True**.</span><span class="sxs-lookup"><span data-stu-id="05203-174">This problem can occur if the published orchestration contains a schema with one or more fields that have a **Data Type** of **xs:date** and a **Nillable** property of **True**.</span></span>  
  
#### <a name="workaround"></a><span data-ttu-id="05203-175">Pour contourner le problème</span><span class="sxs-lookup"><span data-stu-id="05203-175">Workaround</span></span>  
 <span data-ttu-id="05203-176">Pour contourner ce problème, recherchez les champs du schéma publié qui ont un **Type de données** de **xs : date** et vérifiez que le **Nillable** de ces champs est définie sur **False**.</span><span class="sxs-lookup"><span data-stu-id="05203-176">To workaround this problem, locate the fields in the published schema that have a **Data Type** of **xs:date** and verify that the **Nillable** property of these fields is set to **False**.</span></span>  
  
### <a name="a-systemiofilenotfoundexception-error-occurs-when-a-web-service-is-called"></a><span data-ttu-id="05203-177">Une erreur « System.IO.FileNotFoundException » se produit lorsqu'un service Web est appelé.</span><span class="sxs-lookup"><span data-stu-id="05203-177">A "System.IO.FileNotFoundException" error occurs when a Web service is called</span></span>  
  
#### <a name="problem"></a><span data-ttu-id="05203-178">Problème</span><span class="sxs-lookup"><span data-stu-id="05203-178">Problem</span></span>  
 <span data-ttu-id="05203-179">Lorsque vous appelez un service Web dans une application Web Microsoft ASP.NET, il est possible que vous receviez l'erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="05203-179">When you call a Web service in a Microsoft ASP.NET Web application, you may receive the following error:</span></span>  
  
 <span data-ttu-id="05203-180">System.IO.FileNotFoundException</span><span class="sxs-lookup"><span data-stu-id="05203-180">System.IO.FileNotFoundException</span></span>  
  
#### <a name="cause"></a><span data-ttu-id="05203-181">Cause</span><span class="sxs-lookup"><span data-stu-id="05203-181">Cause</span></span>  
 <span data-ttu-id="05203-182">Cette erreur peut se produire si l'une des conditions suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="05203-182">This error can occur if either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="05203-183">Le processus de travail ne dispose ni des autorisations pour lire le répertoire temporaire de processus ni des autorisations pour écrire dans le répertoire temporaire de processus.</span><span class="sxs-lookup"><span data-stu-id="05203-183">The worker process does not have permissions to read to the process Temp directory, and the worker process does not have permissions to write to the process Temp directory.</span></span>  
  
-   <span data-ttu-id="05203-184">Le code généré par XmlSerializer contient des erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="05203-184">There are compilation errors in the code that XmlSerializer generated.</span></span>  
  
#### <a name="resolution"></a><span data-ttu-id="05203-185">Résolution</span><span class="sxs-lookup"><span data-stu-id="05203-185">Resolution</span></span>  
 <span data-ttu-id="05203-186">Cette erreur est documentée dans l’article de la Base de connaissances Microsoft [823196](http://support.microsoft.com/kb/823196).</span><span class="sxs-lookup"><span data-stu-id="05203-186">This error is documented in Microsoft Knowledge Base article [823196](http://support.microsoft.com/kb/823196).</span></span> <span data-ttu-id="05203-187">Suivez les étapes de la section Résolution de cet article pour corriger cette erreur.</span><span class="sxs-lookup"><span data-stu-id="05203-187">Follow the steps in the Resolution section of this Knowledge Base article to resolve this error.</span></span>