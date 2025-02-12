pipeline {
agent any
stages {
stage('Build') {
steps {
sh 'echo "Hello World"'
sh '''
echo "Multiline shell steps works too"
ls -lah
'''
}
}
stage('Upload to AWS') {
steps {
withAWS(region:'us-east-1',credentials:'prabhu-jenkins') {
sh 'echo "Uploading content with AWS creds"'
s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'WildWanderes.css',
bucket:'myjenkinss3')
}
}
}
}
}
Step 5: Setup Pipeline
Now is the time to put the final piece into its place to build the project. Now we will create our
pipeline. From the left pane, select New Item. Enter a new item name and select Pipeline as the
item type.

