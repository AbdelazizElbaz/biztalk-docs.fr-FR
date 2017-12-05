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
ms.openlocfilehash: f1b768bf667969c4adc8119b6d9d89c0ed79fc32
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshooting-biztalk-web-services"></a>Dépannage des services Web BizTalk
Cette section explique comment identifier et résoudre les problèmes courants relatifs aux services Web.  
  
## <a name="general-troubleshooting"></a>Dépannage d'ordre général  
  
### <a name="enabling-web-services-publishing-wizard-tracing"></a>Activation du suivi de l'Assistant Publication de services Web  
 Vous pouvez activer le suivi pour déboguer l’Assistant de publication des Services Web BizTalk en supprimant commentaires le \<ajouter\> nœud dans le fichier BTSWebSvcWiz.exe.config. Pour plus d’informations sur l’obtention des informations de trace à partir de l’Assistant Publication de Services Web, consultez [comment modifier les BTSWebSvcWiz.exe.config](../core/how-to-modify-btswebsvcwiz-exe-config.md).  
  
### <a name="enabling-soap-message-tracing"></a>Activation du suivi de message SOAP  
 Vous pouvez activer le suivi de message SOAP pour déboguer l'application de publication de services Web à l'aide d'une extension SOAP. Pour plus d’informations sur les extensions SOAP, consultez [Comment : implémenter une Extension SOAP](http://go.microsoft.com/fwlink/?LinkId=62314).  
  
### <a name="using-the-throwdetailederror-switch"></a>Utilisation du commutateur ThrowDetailedError  
 Si une erreur se produit, le client Web reçoit un générique **SoapException**.  
  
 Pour déboguer votre service Web publié, vous pouvez ajouter un commutateur au fichier web.config pour contrôler le niveau de détails de l’exception retournée par le service Web publié. Le commutateur est **ThrowDetailedError**, et si elle est définie **True** le serveur proxy retourne des informations sur l’exception interne au client Web, ce qui vous permet de déboguer le service Web publié.  
  
 Le code XML suivant montre la **ThrowDetailedError** commutateur qui apparaît dans le fichier web.config sous le \<appSettings\> nœud :  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!WARNING]
>  L'exception interne peut contenir des données sensibles. Après le débogage, vous devez définir le **ThrowDetailedError** basculer vers **False**.  
  
### <a name="using-net-framework-tracing-to-capture-and-log-errors-in-the-web-service"></a>Utilisation du suivi .NET Framework pour capturer et consigner les erreurs du service Web  
 Le .NET Framework **System.Diagnostics.Trace** classe peut être utilisée pour capturer et écrire les erreurs dans un fichier texte.  
  
##### <a name="to-use-the-systemdiagnosticstrace-class-to-capture-and-write-errors-to-a-text-file"></a>Utilisation de la classe System.Diagnostics.Trace pour capturer et écrire les erreurs dans un fichier texte  
  
1.  Mettre à jour le fichier web.config pour le service Web définir la directive de compilateur TRACE sur **true** et ajoutez un **TraceSwitch** valeur :  
  
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
    >  Si la directive de compilateur TRACE n’est pas définie sur **true** , aucune sortie de trace ne sera généré. Le **TraceSwitch** valeur peut également être définie dans la classe appelante mais est définie ici dans le fichier web.config pour des raisons pratiques. Définir le **TraceSwitch** valeur au niveau approprié pour le développement et modifiez la valeur issue du développement afin de réduire ou désactiver la sortie de trace.  
  
2.  Créez une instance de la **TraceSwitch** et **TextWriterTraceListener** classes et utiliser un **try... catch** bloquer dans l’appel de service [WebMethod] Web pour intercepter et écrire les erreurs dans un fichier de sortie de trace. Par exemple, le code suivant intercepte une erreur qui est générée lors de la tentative de définition de la variable entière s2 sur une instance null de la variable objet o2 :  
  
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
    >  Ce code est une version modifiée du service HelloWorld Web qui est généré par défaut lorsque vous créez un nouveau **Service Web ASP.Net** projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
    > [!NOTE]
    >  Pour Windows Vista, des privilèges d’administrateur peuvent être nécessaires pour écrire le fichier de sortie de trace dans le dossier racine.  
  
3.  Reconstruisez le projet de service Web. Maintenant, si une erreur se produit dans le **essayez** instruction l’exception est gérée dans le **Catch** instruction et une erreur est écrite dans le fichier de sortie de trace.  
  
## <a name="general-troubleshooting-questions-and-answers"></a>Questions et réponses d'ordre général sur le dépannage  
 Cette section présente un certain nombre de questions et réponses conçues pour vous aider à résoudre les problèmes liés aux services Web.  
  
### <a name="i-am-receiving-errors-when-consuming-a-web-service-how-can-i-avoid-them"></a>Je reçois des erreurs lorsque j'utilise un service Web. Comment puis-je y remédier ?  
 Vous devez tenir compte de nombreux détails lorsque vous utilisez un service Web, notamment les suivants :  
  
-   Évitez d'utiliser deux caractères de soulignement dans un nom de paramètre.  
  
-   Utilisation de la **tout** élément ou le **anyAttribute** attribut n’est pas pris en charge dans les méthodes Web.  
  
-   Évitez d'utiliser des mots clés XLANG/s comme nom de service ou de méthode Web.  
  
-   Évitez d'utiliser des types de paramètre de méthode Web non pris en charge par XLANG/s.  
  
-   N'utilisez pas de noms d'élément qui sont des mots clés C# ou qui ne sont pas valides en tant qu'identificateur C# dans vos schémas.  
  
-   Évitez les fichiers WSDL (Web Services Description Language) avec plusieurs définitions de service ou de type de port.  
  
-   Paramètres de méthode Web doivent être sérialisables Xml.  
  
-   Évitez toute référence aux services Web utilisés contenant des schémas à plusieurs racines.  
  
-   Évitez de référencer les services Web avec des méthodes Web qui attendent des paramètres basés sur des génériques, tels que des paramètres de type nullable.  
  
-   L'élément d'importation WSDL n'est pas pris en charge.  
  
 Pour plus d’informations sur ces éléments et autres considérations connexes, consultez [Considérations lors de la consommation des Services Web](../core/considerations-when-consuming-web-services.md).  
  
### <a name="why-am-i-getting-errors-publishing-my-schema-that-uses-the-include-element"></a>Pourquoi les erreurs de publication mon schéma qui utilise le \<incluent\> élément ?  
 Schémas ne peut pas être publiées si elles comprennent les références circulaires (le schéma inclus a un **incluent** élément vers le schéma, y compris) ou avoir un non résolue **schemaLocation** attribut.  
  
 Pour plus d’informations sur la limitation de la **incluent** élément, consultez [Include Element Binding Support](http://go.microsoft.com/fwlink/?LinkId=62312). L’Assistant Publication de Services Web a les mêmes limitations que XSD.exe dans .NET Framework 2.0 ; Pour plus d’informations, consultez [Import Element Binding Support](http://go.microsoft.com/fwlink/?LinkId=119606).  
  
### <a name="why-do-i-receive-errors-when-publishing-my-envelope-schema"></a>Je reçois des erreurs lors de la publication de mon schéma d'enveloppe. Pourquoi ?  
 Si vous publiez un schéma d'enveloppe en tant que service Web, vous devez modifier manuellement le projet Web généré.  
  
##### <a name="to-modify-the-generated-web-project-for-envelope-schemas"></a>Pour modifier le projet Web généré pour les schémas d'enveloppe  
  
1.  Ouvrez le  *\<myWebService\>*. asmx.cs fichier.  
  
2.  Éditez le fichier et changez la valeur de `bodyTypeAssemblyQualifiedName = <dll.name.version>` en `bodyTypeAssemblyQualifiedName = null`  
  
> [!NOTE]
>  Il peut être nécessaire de réinitialiser les services Internet (IIS) si le précédent fichier .dll est toujours présent dans le processus de travail ASP.NET.  
  
### <a name="clients-of-published-web-services-may-not-receive-server-script-time-out-errors"></a>Les clients de services Web publiés peuvent ne pas recevoir d'erreurs d'expiration de script de serveur.  
 Si des clients Web utilisant .NET Framework appellent un service Web généré avec l'Assistant Publication de services Web [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est possible que le client ne puisse pas recevoir d'erreurs d'expiration de script de serveur, l'expiration de la requête du client se produisant en premier par défaut. Pour résoudre ce problème, vous pouvez effectuer une des opérations suivantes :  
  
-   Augmenter le délai d’attente de demande client pour une valeur supérieure au délai d’expiration de script de serveur en augmentant la valeur de la **HttpWebRequest.Timeout** propriété sur le client.  
  
-   Réduire le délai d’expiration de script de serveur à une valeur inférieure au délai d’attente de la demande client en réduisant la valeur pour le **HttpServerUtility.ScriptTimeout** propriété sur le serveur.  
  
## <a name="common-errors"></a>Erreurs fréquentes  
  
### <a name="a-web-service-returns-an-http-404-file-not-found-error"></a>Un service Web retourne une erreur HTTP 404 (fichier introuvable).  
  
#### <a name="problem"></a>Problème  
 Les tentatives d'appel d'un service Web renvoient une erreur HTTP 404 (fichier introuvable).  
  
#### <a name="cause"></a>Cause  
 Cette erreur peut se produire si ASP.NET n'est pas installé et/ou activé sur le serveur IIS qui héberge le service Web.  
  
#### <a name="resolution"></a>Résolution  
 Assurez-vous qu'ASP.NET est installé et activé. Installez .NET Framework s'il n'est pas déjà installé et/ou exécutez le programme aspnet_regiis.exe situé dans le dossier %WinDir%\Microsoft.NET\Framework\vXXX.XXX\ du serveur IIS.  
  
### <a name="date-fields-are-removed-from-documents-processed-by-a-web-service-generated-with-the-biztalk-server-web-services-publishing-wizard"></a>Les champs de date sont supprimés des documents traités par un service Web généré avec l'Assistant Publication de services Web de BizTalk Server.  
  
#### <a name="problem"></a>Problème  
 Lorsque vous traitez un document avec un service web qui a été généré avec le BizTalk Server Web Assistant Publication de Services, les données contenues dans un champ avec un **Type de données** de **xs : date** est supprimé de la document.  
  
#### <a name="cause"></a>Cause  
 Ce problème peut se produire si l’orchestration publiée contient un schéma avec un ou plusieurs champs qui ont un **Type de données** de **xs : date** et un **Nillable** propriété de  **True**.  
  
#### <a name="workaround"></a>Pour contourner le problème  
 Pour contourner ce problème, recherchez les champs du schéma publié qui ont un **Type de données** de **xs : date** et vérifiez que le **Nillable** de ces champs est définie sur **False**.  
  
### <a name="a-systemiofilenotfoundexception-error-occurs-when-a-web-service-is-called"></a>Une erreur « System.IO.FileNotFoundException » se produit lorsqu'un service Web est appelé.  
  
#### <a name="problem"></a>Problème  
 Lorsque vous appelez un service Web dans une application Web Microsoft ASP.NET, il est possible que vous receviez l'erreur suivante :  
  
 System.IO.FileNotFoundException  
  
#### <a name="cause"></a>Cause  
 Cette erreur peut se produire si l'une des conditions suivantes est vraie :  
  
-   Le processus de travail ne dispose ni des autorisations pour lire le répertoire temporaire de processus ni des autorisations pour écrire dans le répertoire temporaire de processus.  
  
-   Le code généré par XmlSerializer contient des erreurs de compilation.  
  
#### <a name="resolution"></a>Résolution  
 Cette erreur est documentée dans l’article de la Base de connaissances Microsoft [823196](http://support.microsoft.com/kb/823196). Suivez les étapes de la section Résolution de cet article pour corriger cette erreur.