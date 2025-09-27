AWSTemplate CloudFormation.
Descrição: Criar três instâncias EC2 t3.micro em 3 regiões diferentes e usar o CodeDeploy para implantar uma API.

      Parameters:
      InstanceType:
        Description: Tipo da instância EC2
        Type: String
        Default: t3.micro
        AllowedValues:
          - t3.micro
          - t2.micro
        ConstraintDescription: Deve ser um tipo de instância EC2 válido.
    
    Resources:
      # EC2 Instances
      Instance1:
        Type: AWS::EC2::Instance
        Properties:
          ImageId: ami-0abcdef1234567890 # Substituir pelo ID da AMI na região  desejada
          InstanceType: !Ref InstanceType
          KeyName: your-key-pair # Inserir a key pair
          Tags:
            - Key: Name
              Value: Instance1-Region1
    
      Instance2:
        Type: AWS::EC2::Instance
        Properties:
          ImageId: ami-0abcdef1234567890 # Substituir pelo ID da AMI na região desejada
          InstanceType: !Ref InstanceType
          KeyName: your-key-pair # Inserir a key pair
          Tags:
            - Key: Name
              Value: Instance2-Region2
    
      Instance3:
        Type: AWS::EC2::Instance
        Properties:
          ImageId: ami-0abcdef1234567890 # Substituir pelo ID da AMI na região desejada
          InstanceType: !Ref InstanceType
          KeyName: your-key-pair # Inserir a key pair
          Tags:
            - Key: Name
              Value: Instance3-Region3
    
      # AWS CodeDeploy
      CodeDeployApplication:
        Type: AWS::CodeDeploy::Application
        Properties:
          ApplicationName: MyApiApplication
          ComputePlatform: Server
    
      CodeDeployDeploymentGroup:
        Type: AWS::CodeDeploy::DeploymentGroup
        Properties:
          ApplicationName: !Ref CodeDeployApplication
          ServiceRoleArn: arn:aws:iam::123456789012:role/CodeDeployRole # Substitua pelo ARN correto do seu IAM role
          DeploymentStyle:
            DeploymentType: IN_PLACE
            Stack: 'my-stack' # Nome do stack
          HealthCheckPack:
            ComputePlatform: Server
            Interval: '300'
          BlueGreenDeploymentConfiguration: {}
    
      # IAM Role for CodeDeploy
      CodeDeployRole:
        Type: AWS::IAM::Role
        Properties:
          AssumeRolePolicyDocument:
            Version: '2012-10-17'
            Statement:
              - Effect: Allow
                Principal:
                  Service: codedeploy.amazonaws.com
                Action: sts:AssumeRole
          Policies:
            - PolicyName: CodeDeployPolicy
              PolicyDocument:
                Version: '2012-10-17'
                Statement:
                  - Effect: Allow
                    Action:
                      - codedeploy:*
                      - s3:ListBucket
                      - s3:GetObject
                    Resource: "*"
    
    Outputs:
      Instance1Output:
        Description: "ID da instância 1"
        Value: !Ref Instance1
    
      Instance2Output:
        Description: "ID da instância 2"
        Value: !Ref Instance2
    
      Instance3Output:
        Description: "ID da instância 3"
        Value: !Ref Instance3
