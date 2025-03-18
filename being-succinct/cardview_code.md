// MARK: Card List
          if let cardListView = self.cardListView {
             self.contentVStackView.removeArrangedSubview(cardListView)
          }
          let functionResponse = json["function_response"]
          if functionResponse.type != .null {
             let statusCode = functionResponse["status_code"].intValue
             let endpoint = functionResponse["endpoint"].stringValue
             let response = functionResponse["response"]
             if statusCode == 200 {
                 if ... {
                   ...
                 } else if endpoint.contains("/reservation") {
                     // Replace the message text with the custom text
                     customText = "Your appointment has been successfully scheduled. Here are the details"
                     SBUGlobalCustomParams.cardViewParamsCollectionBuilder = { messageData in
                         guard
                             let data = messageData.data(using: .utf8),
                             let json = try? JSON(data: data)
                         else { return [] }
                         // Convert the single order object into a SBUCardViewParams object
                         let orderParams = SBUCardViewParams(
                             imageURL: nil,
                             title: "Date: \(json["appointmentDetails"]["date"].stringValue):\(json["appointmentDetails"]["time"].stringValue)",
                             subtitle: nil,
                             description: "- ID: \(json["appointmentDetails"]["appointmentId"].stringValue)\n- Department: \(json["appointmentDetails"]["department"].stringValue)\n- Doctor: \(json["appointmentDetails"]["doctor"].stringValue)",
                             link: nil
                         )
                         return [orderParams]
                     }
                     if let items = try?SBUGlobalCustomParams.cardViewParamsCollectionBuilder?(response.rawString()!){
                         self.addCardListView(with: items)
                     }
                 } else if endpoint.contains("/recommend_date") {
                     // Replace the message text with the custom text
                     customText = "Here are the available appointment date and time."
                     disableWebview = true
                     SBUGlobalCustomParams.cardViewParamsCollectionBuilder = { messageData in
                         guard
                             let data = messageData.data(using: .utf8),
                             let json = try? JSON(data: data)
                         else { return [] }
                         return json.arrayValue.compactMap { item in
                             return SBUCardViewParams(
                                     imageURL: nil,
                                     title: "\(item["doctor"].stringValue)",
                                     subtitle: "Date: \(item["recommend_date"].stringValue)",
                                     description: nil,
                                     link: nil,
                                     actionHandler: {
                                         self.cardSelectHandler!("Please reserve a reservation with \(item["doctor"].stringValue), \(item["recommend_date"].stringValue)")
                                     }
                             )
                         }
                     }
                     if let items = try?SBUGlobalCustomParams.cardViewParamsCollectionBuilder?(response.rawString()!){
                         self.addCardListView(with: items)
                     }
                 }
             }
          } else {
             self.cardListView = nil
          }
