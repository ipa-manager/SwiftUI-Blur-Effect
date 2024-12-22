import SwiftUI
import UIKit

struct BlurView: UIViewRepresentable {
    var intensity: CGFloat
    var style: UIBlurEffect.Style
    var vibrancyEffect: Bool
    var tintColor: UIColor?
    
    func makeUIView(context: Context) -> UIVisualEffectView {
        let blurEffect = UIBlurEffect(style: style)
        let blurView = UIVisualEffectView(effect: blurEffect)
        blurView.alpha = intensity
        
        if vibrancyEffect {
            let vibrancyEffectView = UIVisualEffectView(effect: UIVibrancyEffect(blurEffect: blurEffect))
            vibrancyEffectView.frame = blurView.bounds
            vibrancyEffectView.autoresizingMask = [.flexibleWidth, .flexibleHeight]
            blurView.contentView.addSubview(vibrancyEffectView)
        }
        
        // Optional tint color
        if let tintColor = tintColor {
            blurView.backgroundColor = tintColor.withAlphaComponent(0.2)
        }
        
        return blurView
    }
    
    func updateUIView(_ uiView: UIVisualEffectView, context: Context) {
        uiView.alpha = intensity
        if let tintColor = tintColor {
            uiView.backgroundColor = tintColor.withAlphaComponent(0.2)
        }
    }
}

struct BlurEffect: ViewModifier {
    var intensity: CGFloat
    var style: UIBlurEffect.Style
    var vibrancyEffect: Bool
    var tintColor: UIColor?
    
    func body(content: Content) -> some View {
        content
            .background(BlurView(intensity: intensity, style: style, vibrancyEffect: vibrancyEffect, tintColor: tintColor))
    }
}

// Extension for easier use of the modifier
extension View {
    func blurEffect(intensity: CGFloat, style: UIBlurEffect.Style = .regular, vibrancyEffect: Bool = false, tintColor: UIColor? = nil) -> some View {
        self.modifier(BlurEffect(intensity: intensity, style: style, vibrancyEffect: vibrancyEffect, tintColor: tintColor))
    }
}
