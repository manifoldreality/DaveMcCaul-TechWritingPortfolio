// MARK: Quick Reply        
          if let quickReplyView = self.quickReplyView {
              quickReplyView.removeFromSuperview()
              self.quickReplyView = nil
          }
          if let replyOptions = message.quickReply?.options, !replyOptions.isEmpty {
              self.updateQuickReplyView(with: replyOptions)
          }
