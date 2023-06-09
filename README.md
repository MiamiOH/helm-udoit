# helm-template

The chart source can be found here: https://github.com/miamioh/helm-template

## Introduction

[Helm](https://helm.sh/) is a package manager for Kubernetes. A Helm chart has been written to more easily deploy UDOIT to containers on a Kubernetes cluster.

## Prerequisites

* A deployed Kubernetes cluster
* Your Kubernetes cluster must have the [Ingress NGINX Controller](https://github.com/kubernetes/ingress-nginx) installed
* A working knowledge of installation with Helm, e.g. the `helm install...` command. More information can be found at [Install an Example Chart](https://helm.sh/docs/intro/quickstart/#install-an-example-chart) or the general [Helm documentation](https://helm.sh/docs/)

## Installing the Chart

Add the repository: `helm repo add miamioh-udoit https://miamioh.github.io/helm-udoit`

To install the chart with the release name `my-release`:

```console
helm install miamioh-udoit/udoit --name my-release
```

The [configuration](#configuration) section lists the parameters that can be configured during installation.

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release
```

The command removes the Helm deployment associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the heml-template chart and their default values.

| Parameter | Description | Default Value
| --- | --- | --- |
| `app.env` | Application environment | `prod`
| `app.host` | The URL of your instance of UDOIT | `127.0.0.1:8000`
| `app.admin_lti_name` | lorem ipsum | `UDOIT 3 Admin`
| `app.lms` | The name of your LMS; `canvas` if you are using the Canvas LMS or `d2l` if you are using the D2l Brightspace LMS | `canvas`
| `app.app_lti_name` | lorem ipsum | `UDOIT 3`
| `app.app_lti_redirect_path` | lorem ipsum | `/lti/authorize/check`
| `app.app_oauth_redirect_path` | lorem ipsum | `/authorize/check`
| `app.secret` | lorem ipsum | `eb2f09f8a21b0b7c57b9fc36eee250eb`
| `app.jwk_base_url` | lorem ipsum | `https://canvas.instructure.com/`
| `app.messenger_transport_dsn` | lorem ipsum | `doctrine://default`
| `app.lti_name` | lorem ipsum | `UDOIT 3`
| `app.auditory_rules` | lorem ipsum | `AnchorLinksToMultiMediaRequireTranscript,AnchorLinksToSoundFilesNeedTranscripts,ObjectMustContainText,ObjectTagDetected,VideoCaptionsMatchCourseLanguage,VideoEmbedCheck,VideoProvidesCaptions,VideosEmbeddedOrLinkedNeedCaptions,VideosEmbeddedOrLinkedNeedCaptions,VideosHaveAutoGeneratedCaptions`
| `app.background_color` | lorem ipsum | `#ffffff`
| `app.cognitive_rules` | lorem ipsum | `BaseFontIsNotUsed,BlinkIsNotUsed,ContentTooLong,DocumentReadingDirection,FontIsNotUsed,HeadingsInOrder,MarqueeIsNotUsed,NoHeadings,ObjectTagDetected,ParagraphNotUsedAsHeader,TableDataShouldHaveTableHeader,TableHeaderShouldHaveScope`
| `app.date_format` | Date format | `Y-m-d`
| `app.default_lang` | Default language | `en`
| `app.easy_fix_rules` | lorem ipsum | `AnchorMustContainText,AnchorSuspiciousLinkText,CssTextHasContrast,CssTextStyleEmphasize,HeadersHaveText,ImageAltIsDifferent,ImageAltIsTooLong,ImageHasAlt,ImageHasAltDecorative,ParagraphNotUsedAsHeader,ImageAltNotPlaceholder`
| `app.motor_rules` | lorem ipsum | `ObjectTagDetected`
| `app.phpally_excluded_rules` | phpally rules to exclude | `BrokenLink,RedirectedLink`
| `app.phpally_suggestion_rules` | lorem ipsum | `AnchorLinksToMultiMediaRequireTranscript,AnchorLinksToSoundFilesNeedTranscripts,AnchorSuspiciousLinkText,ContentTooLong,IframeNotHandled,InputImageNotDecorative,NoHeadings,ObjectTagDetected,ParagraphNotUsedAsHeader,PreShouldNotBeUsedForTabularValues,RedirectedLink,EmbedTagDetected,IframeNotHandled`
| `app.store_user_names` | lorem ipsum | `true`
| `app.text_color` | lorem ipsum | `#2D3B45`
| `app.use_development_auth` | lorem ipsum | `no`
| `app.version_number` | UDOIT veersion | `3.3.0`
| `app.vimeo_api_key` | Vimeo API access key | `null`
| `app.visual_rules` | lorem ipsum | `AnchorMustContainText,AnchorSuspiciousLinkText,BaseFontIsNotUsed,CssTextHasContrast,CssTextStyleEmphasize,FontIsNotUsed,HeadersHaveText,HeadingsInOrder,ImageAltIsDifferent,ImageAltIsTooLong,ImageAltNotEmptyInAnchor,ImageAltNotPlaceholder,ImageHasAlt,ImageHasAltDecorative,ImageHasLongDescription,InputImageNotDecorative,NoHeadings,ObjectTagDetected,ParagraphNotUsedAsHeader,PreShouldNotBeUsedForTabularValues,TableDataShouldHaveTableHeader,TableHeaderShouldHaveScope`
| `app.youtube_api_key` | YouTube API access key | `null`

### Other important Values

#### Database Configuration Settings

| Parameter | Description | Default Value
| --- | --- | --- |
| `database.type` | The database type | `mysql`
| `database.host` | The database host | `db`
| `database.port` | Database port in use | `"3306"`
| `database.user` | Database user name | `root`
| `database.name` | The name of the UDOIT database | `udoit3`
| `database.password` | Database user password | `root`

#### Other Configuration Settings

| Parameter | Description | Default Value
| --- | --- | --- |
| `image.tag` | Overrides the image tag whose default is the chart appVersion. | `"main"`


### How-to Specify parameter values

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install miamioh-udoit/helm-template --name my-release \
  --set=image.repository=my-image
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
helm install miamioh/helm-template --name my-release -f values.yaml
```

> **Tip**: You can use the default [values.yaml](values.yaml)
