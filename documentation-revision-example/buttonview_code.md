// MARK: ButtonView
          if let buttonView = self.buttonView {
              self.contentVStackView.removeArrangedSubview(buttonView)
          }
          let functionResponse = json["function_response"]
          if functionResponse.type != .null {
              let statusCode = functionResponse["status_code"].intValue
              let endpoint = functionResponse["endpoint"].stringValue
              let response = functionResponse["response"]
              if statusCode == 200 {
                  if endpoint.contains("/check_availability_of_doctor_for_consultation") {
                     // Replace the message text with the custom text
                     customText = "Yes, you can talk to a doctor. "
                     let buttonParams = SBUButtonViewParams(
                         actionText: "Invite a Doctor",
                         description: "If you want to talk to a doctor, please click the button!",
                         actionHandler: {
                             self.buttonClicked = true
                             self.buttonSelectHandler!()
                             self.layoutIfNeeded()
                         },
                         enableButton: !shouldHideButton && !self.buttonClicked,
                         disableButtonText: "In Progress"
                     )
                     self.updateButtonView(with: buttonParams)
                  } 
                  ...
              }
          }
