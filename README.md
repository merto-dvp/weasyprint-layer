
# WeasyPrint layer for AWS Lambda




# Build Lambda Layer

Run create_layer.sh to build weasyprint layer.

Deploy layer:

    $ aws lambda publish-layer-version \
        --region <region> \
        --layer-name <name> \
        --zip-file fileb://build/weasyprint-layer-python3.8.zip

Environment variables expected by layer:

    GDK_PIXBUF_MODULE_FILE="/opt/lib/loaders.cache"
    FONTCONFIG_PATH="/opt/fonts"
    XDG_DATA_DIRS="/opt/lib"

Add environment variables to template.yml

      Environment:
        Variables:
          GDK_PIXBUF_MODULE_FILE: "/opt/lib/loaders.cache"
          FONTCONFIG_PATH: "/opt/fonts"
          XDG_DATA_DIRS: "/opt/lib"
