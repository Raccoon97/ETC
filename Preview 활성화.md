# SwiftUI 에서 사용하던 Preview 기능을 마음대로 사용해보자!

```txt
@available : TargetVersion

PreviewDevice(rawValue: TargetDevice) 또는 PreviewDevice(stringLiteral: TargetDevice)


* 코드 작성 후 Preview 가 보이지 않는다면, Option + Cmd + P ( ⌥ + ⌘ + P )
```
```swift
#if DEBUG
import SwiftUI

struct ViewControllerRepresentable: UIViewControllerRepresentable {
    func updateUIViewController(_ uiViewController: UIViewControllerType, context: Context) { }
    
    @available(iOS 16.0, *)
    func makeUIViewController(context: Context) -> some UIViewController {
        ViewController()
    }
}
@available(iOS 16.0, *)
struct SnapKitVCRepresentable_PreviewProvider: PreviewProvider {
    static var previews: some View {
        Group {
            ViewControllerRepresentable()
                .ignoresSafeArea()
                .previewDisplayName("Preview")
                .previewDevice(PreviewDevice(rawValue: "iPhone 14 Pro"))
        }
    }
}
#endif
```
