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
# <a name="troubleshooting-web-services"></a>Dépannage des Services Web
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exploite pleinement les services Web dans le cadre de l'utilisation de l'adaptateur SOAP et lors de la publication d'orchestrations en tant que services Web. Cette rubrique propose des procédures à suivre pour résoudre les problèmes liés aux services Web que vous êtes le plus susceptible de rencontrer.  
  
## <a name="use-net-framework-tracing-to-capture-and-log-errors-in-a-web-service"></a>Utilisation du suivi .NET Framework pour capturer et consigner les erreurs d'un service Web  
 Le .NET Framework **System.Diagnostics.Trace** classe peut être utilisée pour capturer et écrire les erreurs dans un fichier texte.  
  
#### <a name="to-use-the-systemdiagnosticstrace-class-to-capture-and-write-errors-to-a-text-file"></a>Utilisation de la classe System.Diagnostics.Trace pour capturer et écrire les erreurs dans un fichier texte  
  
1.  Mettre à jour le fichier web.config pour le service Web définir le **TRACE** directive de compilateur pour **true** et ajoutez un **TraceSwitch** valeur :  
  
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
    >  Si le **TRACE** directive de compilateur n’est pas définie sur **true** , aucune sortie de trace ne sera généré. Le **TraceSwitch** valeur peut également être définie dans l’appel de la classe, mais est définie ici dans le fichier web.config pour des raisons pratiques. Définir le **TraceSwitch** valeur au niveau approprié pour le développement et modifiez la valeur issue du développement afin de réduire ou désactiver la sortie de trace.  
  
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
                Trace.WriteLineIf(WebSvcTraceSwitch.Level = TraceLevel.Warning, "Exception caught: " + e.Message);  
                //Writes to the trace file if specified TraceLevel switch value (in web.config) >= 2  
                TestTracer.Dispose();  
                return "An error occurred in the Web service, please contact the web server administrator.";  
            }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  Ce code est une version modifiée de la valeur par défaut du service HelloWorld Web qui est généré lorsque vous créez un nouveau **Service Web ASP.Net** projet dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
    > [!NOTE]
    >  Pour Windows Vista, des privilèges d’administrateur peuvent être nécessaires pour écrire le fichier de sortie de trace dans le dossier racine.  
  
3.  Reconstruisez le projet de service Web. Maintenant, si une erreur se produit dans le **essayez** instruction l’exception est gérée dans le **Catch** instruction et une erreur est écrite dans le fichier de sortie de trace.  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="a-web-service-returns-an-http-404-file-not-found-error"></a>Un service Web retourne une erreur HTTP 404 (fichier introuvable).  
  
##### <a name="problem"></a>Problème  
 Les tentatives d'appel d'un service Web renvoient une erreur HTTP 404 (fichier introuvable).  
  
##### <a name="cause"></a>Cause  
 Cette erreur peut se produire si ASP.NET n'est pas installé et/ou activé sur le serveur IIS qui héberge le service Web.  
  
##### <a name="resolution"></a>Résolution  
 Assurez-vous qu'ASP.NET est installé et activé. Installer le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] si elle n’est pas installé et/ou exécutez le **aspnet_regiis.exe** programme situé dans le %WinDir%\Microsoft.NET\Framework\\*vXXX.XXX*\ dossier du serveur IIS.  
  
#### <a name="a-systemiofilenotfoundexception-error-occurs-when-a-web-service-is-called"></a>Une erreur « System.IO.FileNotFoundException » se produit lorsqu'un service Web est appelé.  
  
##### <a name="problem"></a>Problème  
 Lorsque vous appelez un service Web dans une application Web Microsoft ASP.NET, il est possible que vous receviez l'erreur suivante :  
  
 **System.IO.FileNotFoundException**  
  
##### <a name="cause"></a>Cause  
 Cette erreur peut se produire si l'une des conditions suivantes est vraie :  
  
-   Le processus de travail ne dispose ni des autorisations pour lire le répertoire temporaire de processus ni des autorisations pour écrire dans le répertoire temporaire de processus.  
  
-   Le code généré par XmlSerializer contient des erreurs de compilation.  
  
##### <a name="resolution"></a>Résolution  
 Cette erreur est documentée dans la Base de connaissances Microsoft l’article 823196, [PRB : vous recevez un « System.IO.FileNotFoundException » erreur lorsque le Client Application appelle un Service Web](http://go.microsoft.com/fwlink/?LinkID=84694)». Suivez les étapes de la section Résolution de cet article pour corriger cette erreur.  
  
#### <a name="date-fields-are-removed-from-documents-processed-by-a-web-service-generated-with-the-biztalk-server-web-services-publishing-wizard"></a>Les champs de date sont supprimés des documents traités par un service Web généré avec l'Assistant Publication de services Web de BizTalk Server.  
  
##### <a name="problem"></a>Problème  
 Lorsque vous traitez un document avec un service web qui a été généré avec le BizTalk Server Web Assistant Publication de Services, les données contenues dans un champ avec un **Type de données** de **xs : date** et un  **Nillable** propriété du **True** est supprimé du document.  
  
##### <a name="cause"></a>Cause  
 Ce problème est lié à un problème connu relatif à la classe XmlSerializer, qui est disponible avec l'espace de noms de la Bibliothèque de classes Microsoft .NET Framework System.Xml.Serialization.  
  
##### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, installez le correctif .NET Framework 2.0 documenté dans la Base de connaissances Microsoft l’article 925272, «[FIX : sérialisation XML le risque de perdre certains éléments facultatifs dans un schéma XSD dans le .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkId=84696)».  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions pour la résolution des problèmes d’autorisation IIS](../core/guidelines-for-resolving-iis-permissions-problems.md)   
 [Instructions pour la résolution des problèmes d’autorisations Web Services](../core/guidelines-for-resolving-web-services-permissions-problems.md)