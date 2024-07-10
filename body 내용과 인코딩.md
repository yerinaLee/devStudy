# body 원본
{
  "type": "messageCard", 
  "attachments": [
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
        "type": "AdaptiveCard",
        "msteams": {
            "width": "Full"
        },
        "version": "1.2",
        "body": [
          {
            "type": "TextBlock",
            "text": "Test-yeri",
            "weight": "bolder",
            "size": "large"
          },
          {
            "type": "TextBlock",
            "text": "${game.gameName} > ${user.username}",
            "weight": "bolder",
            "size": "medium"
          },
          {
            "type": "TextBlock",
            "text": "${flagQAServer}${inquiryTitle}",
            "wrap": true,
            "maxWidth": "1200px"  
          },
          {
            "type": "FactSet",
            "facts": [
              {
                "title": "Category",
                "value": "${CSCategory.findByCategoryNo(userInquiry.subCategoryNo)}"
              },
              {
                "title": "Content",
                "value": "${inquiryContent}"
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.OpenUrl",
            "title": "Learn More",
            "url": "https://www.naver.com"
          }
        ]
      }
    }
  ]
}



# 인코딩
%7B%22type%22%3A%22messageCard%22%2C%22attachments%22%3A%5B%7B%22contentType%22%3A%22application%2Fvnd.microsoft.card.adaptive%22%2C%22content%22%3A%7B%22%24schema%22%3A%22http%3A%2F%2Fadaptivecards.io%2Fschemas%2Fadaptive-card.json%22%2C%22type%22%3A%22AdaptiveCard%22%2C%22msteams%22%3A%7B%22width%22%3A%22Full%22%7D%2C%22version%22%3A%221.2%22%2C%22body%22%3A%5B%7B%22type%22%3A%22TextBlock%22%2C%22text%22%3A%22Test-yeri%22%2C%22weight%22%3A%22bolder%22%2C%22size%22%3A%22large%22%7D%2C%7B%22type%22%3A%22TextBlock%22%2C%22text%22%3A%22%24%7Bgame.gameName%7D%20%3E%20%24%7Buser.username%7D%22%2C%22weight%22%3A%22bolder%22%2C%22size%22%3A%22medium%22%7D%2C%7B%22type%22%3A%22TextBlock%22%2C%22text%22%3A%22%24%7BflagQAServer%7D%24%7BinquiryTitle%7D%22%2C%22wrap%22%3Atrue%2C%22maxWidth%22%3A%221200px%22%7D%2C%7B%22type%22%3A%22FactSet%22%2C%22facts%22%3A%5B%7B%22title%22%3A%22Category%22%2C%22value%22%3A%22%24%7BCSCategory.findByCategoryNo%28userInquiry.subCategoryNo%29%7D%22%7D%2C%7B%22title%22%3A%22Content%22%2C%22value%22%3A%22%24%7BinquiryContent%7D%22%7D%5D%7D%5D%2C%22actions%22%3A%5B%7B%22type%22%3A%22Action.OpenUrl%22%2C%22title%22%3A%22Learn%20More%22%2C%22url%22%3A%22https%3A%2F%2Fwww.naver.com%22%7D%5D%7D%7D%5D%7D