# Java Feign Client

The `prime-client-java-feign` template generates a Java Feign Client.

## Usage

You can use `docker` to run the generator:

```bash
docker run -it --rm -v $(pwd):/project \
    ghcr.io/primelib/primecodegen:0.0.1 primecodegen generate \
    -e auto \
    -i "/project/openapi.yaml" \
    -o "/project/" \
    -c "/project/openapi-generator.json"
```

## Configuration

Except for the `generatorName`, all values must be replaced with your own values.


``` json title="openapi-generator.json"
{
	"generatorName": "prime-client-java-feign",
	"invokerPackage": "io.github.primelib.<projectName>",
	"apiPackage" : "io.github.primelib.<projectName>.api",
	"modelPackage" : "io.github.primelib.<projectName>.model",
	"enablePostProcessFile": true,
	"additionalProperties": {
		"projectName": "<projectName>",
		"projectDescription": "<projectDescription>",
		"projectRepository":  "github.com/primelib/<projectName>",
		"projectInceptionYear":  "2023",
		"projectLicenseName": "MIT",
		"projectLicenseUrl": "https://github.com/primelib/<projectName>/blob/main/LICENSE",
		"projectArtifactGroupId": "io.github.primelib",
		"projectArtifactId": "<projectName>",
		"projectMaintainerId": "<yourName>",
		"projectMaintainerName": "<yourName>",
		"projectMaintainerEMail": "<yourEMail>",
	}
}
```
