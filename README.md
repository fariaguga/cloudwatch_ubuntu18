<b>RESUMO:</b><br>Configuração do CloudWatch em Ubuntu 18.04 para coleta de estatística.


------------------------------------------------------------------------------

<b>1- </b>Atachar a politica: (CloudWatchMonitoring.json do repositório) na instância que deseja coletar.

------------------------------------------------------------------------------

<b>2-</b> Executar as seguintes linhas no terminal: (usar <b>install_sp.sh</b> se estiver em SP)

cd /tmp<br>
sudo wget https://raw.githubusercontent.com/fariaguga/cloudwatch_ubuntu18/main/install_virginia.sh<br>
sudo chmod +x install_virginia.sh<br>
sudo ./install_virginia.sh<br>

------------------------------------------------------------------------------

<b>3-</b> Aguardar 1 minuto para coleta e depois poderá criar o dashboard para visualização.

------------------------------------------------------------------------------

<b>4-</b> Policy de permissão para o ec2 mandar as métricas para cloudwatch.


{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "cloudwatch:PutMetricData",
                "cloudwatch:GetMetricStatistics",
                "cloudwatch:ListMetrics",
                "ec2:DescribeTags"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "ssm:GetParameter"
            ],
            "Resource": "arn:aws:ssm:*:*:parameter/AmazonCloudWatch-*"
        }
    ]
}
