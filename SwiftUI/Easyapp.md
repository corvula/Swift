```
import SwiftUI

struct ContentView: View{
    @State var tapCount = 0
    @State var buttonText = "Tap Me"
    var body: some View{
        ZStack{
            LinearGradient(
                           gradient: Gradient(colors: [.white, .blue]),
                           startPoint: .top,
                           endPoint: .bottom
                       )
                       .ignoresSafeArea()
            
            VStack(spacing: 20){
                Button(buttonText){
                    tapCount += 1
                }
                .padding()
                .background(Color.blue)
                .foregroundColor(.white)
                .cornerRadius(20)
                .padding(10)
                Text("You tapped me \(tapCount) times")
                
                Button("Restart"){
                    tapCount = 0
                    buttonText = "Tap Me"
                    
                    
                }
            }
        }
    }
}

#Preview {
    ContentView()
}
```
<img width="395" height="565" alt="Знімок екрана 2025-10-05 о 3 32 41 пп" src="https://github.com/user-attachments/assets/bf6309c8-d800-4f56-9d15-78e4b6b5ca16" />
