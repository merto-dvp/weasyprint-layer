
# WeasyPrint layer for AWS Lambda

If you have a python app that uses WeasyPrint and you want to use it with AWS Lambda, you need to create a package that contains requirements. You can use this script to create an AWS Lambda layer package and upload it directly as Layer.


# Build Lambda Layer

Run create_layer.sh to build weasyprint layer.

You can deploy layer with this command. (Requires AWS CLI)

    $ aws lambda publish-layer-version \
        --region <region> \
        --layer-name <name> \
        --zip-file fileb://build/weasyprint-layer-python3.8.zip

Environment variables expected by layer:

    GDK_PIXBUF_MODULE_FILE="/opt/lib/loaders.cache"
    FONTCONFIG_PATH="/opt/fonts"
    XDG_DATA_DIRS="/opt/lib"

You have to add environment variables to template.yml or add directly to Lambda function.

      Environment:
        Variables:
          GDK_PIXBUF_MODULE_FILE: "/opt/lib/loaders.cache"
          FONTCONFIG_PATH: "/opt/fonts"
          XDG_DATA_DIRS: "/opt/lib"
