pipeline {
    agent any

    stages {
        stage('Setup parameters') {
            steps { 
                script {
                    properties([
                        parameters([
                            string(
                                description: "Provide the Accesskey of China RCC GB RRCCCN_AWS_JENKINS Role",
                                name: 'AWSAccessKey'                                
                            ),
                            password(
                                description: "Provide the Secret Accesskey of China RCC GB RRCCCN_AWS_JENKINS Role",
                                name: 'AWSSecretKey'
                            ),
                            password(
                                description: "Provide the Session Token of China RCC GB RRCCCN_AWS_JENKINS Role",
                                name: 'AWSSessionToken'
                            ),
                            choice(
                                description: "Provide the AWS Region",
                                name: 'RegionName',
                                choices: ['cn-north-1']
                            ),
                            string(
                                description: "An identifier for account deployment (e.g.:RDRAECN01, RSSRCN02)",
                                name: 'AccountIdentifier'
                            ),
                            string(
                                description: "Account Number in which services need to be deployed",
                                name: 'AccountName'
                            ),
                            choice(
                                description: "Select the Envrionment Name",
                                name: 'Environment',
                                choices: ['TST','DEV','PGB','GB']
                            ),
                            string(
                                description: "Public Subnet ID for NatGateway AZ1 (e.g. subnet-012719c154949bd11)",
                                name: 'NATSubnetIDAZ11'
                            ),
                            string(
                                description: "Public Subnet ID for NatGateway AZ2 (e.g. subnet-098e8208f00ea9a1d)",
                                name: 'NATSubnetIDAZ21'
                            ),
                            choice(
                                description: "Select integer value indicating the Number of IPs need to add in the route table",
                                name: 'NumberOfIPs',
                                choices: ['1','2','3','4','5','6','7','8','9','10']
                            ),
                            string(
                                description: "Comma-delimited list of CIDR blocks(e.g. 10.0.0.0/16,10.20.0.0/24,...10.30.0.0/24)",
                                name: 'DestinationCIDRIP'
                            ),
                            string(
                                description: "Enter the Private Route Table ID for AZ1 (e.g. rtb-0d3285bdee4a09d4d)",
                                name: 'PrivateRouteTableIDAZ1'
                            )
                            string(
                                description: "Enter the Private Route Table ID for AZ2 (e.g. rtb-093183c3a6b0a3e76)",
                                name: 'PrivateRouteTableIDAZ2'
                            ),
                            string(
                                description: "Provide Account Owner 521 ID",
                                name: 'AccountOwner',
                                defaultValue: 'DIVOUDE1'
                            ),
                            string(
                                description: "Provide Billing Contact 521 id",
                                name: 'BillingContact',
                                defaultValue: 'DIVOUDE1/WIDERRA1'
                            ),
                            string(
                                description: "Provide Clarity ID",
                                name: 'ClarityID',
                                defaultValue: '050520'
                            ),
                            string(
                                description: "Provide CostCenter",
                                name: 'CostCenter',
                                defaultValue: '20ITG0500R'
                            ),
                            string(
                                description: "Provide Owner Name",
                                name: 'Owner',
                                defaultValue: 'Technology and Infrastructure Service'
                            ),
                            choice(
                                description: "Services to be deployed",
                                name: 'ServicesToBeDeployed',
                                choices: ['vpc_natgateway']
                            )
                        ])
                    ])
                }
            }
        }
        stage('Deploy stack') {
            steps {
                    cleanWs()
                    script {
                        sh "bash deploy_stack.sh"
                    }
            }
        }        
    }
}
