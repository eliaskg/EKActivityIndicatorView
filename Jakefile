require('./common.jake');

var ENV = require("system").env,
    FILE = require("file"),
	OS = require("os"),
	JAKE = require("jake"),
    task = JAKE.task,
    CLEAN = require("jake/clean").CLEAN,
    FileList = JAKE.FileList,
    stream = require("narwhal/term").stream,
    framework = require("cappuccino/jake").framework,
    configuration = ENV["CONFIG"] || ENV["CONFIGURATION"] || ENV["c"] || "Release";

framework ("EKActivityIndicatorView", function(task)
{
    task.setBuildIntermediatesPath(FILE.join("Build", "EKActivityIndicatorView.build", configuration));
    task.setBuildPath(FILE.join("Build", configuration));

    task.setProductName("EKActivityIndicatorView");
    task.setIdentifier("org.EKActivityIndicatorView");
    task.setVersion("1.0");
    task.setAuthor("Elias Klughammer");
    task.setEmail("none @nospam@ example.com");
    task.setSummary("EKActivityIndicatorView");
    task.setSources(new FileList("*.j"));
    task.setResources(new FileList("Resources/*"));
    task.setInfoPlistPath("Info.plist");

    if (configuration === "Debug")
        task.setCompilerFlags("-DDEBUG -g");
    else
        task.setCompilerFlags("-O");
});

task("build", ["EKActivityIndicatorView"]);

task("debug", function()
{
    ENV["CONFIG"] = "Debug"
    JAKE.subjake(["."], "build", ENV);
});

task("release", function()
{
    ENV["CONFIG"] = "Release"
    JAKE.subjake(["."], "build", ENV);
});
