Эта змейка на визуал бейсике

Вот код кому надо (говно):

Public Class Form1
    Private Sub Form1_KeyDown(sender As Object, e As KeyEventArgs) Handles MyBase.KeyDown

        Dim panelLocation As Point = snake.Location
        Dim speed As Integer = 10

        Select Case e.KeyCode
            Case Keys.W
                panelLocation.Y -= speed
            Case Keys.A
                panelLocation.X -= speed
            Case Keys.S
                panelLocation.Y += speed
            Case Keys.D
                panelLocation.X += speed
        End Select

        snake.Location = panelLocation
    End Sub

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load

        apple.Location = New Point(New Random().Next(0, 490), New Random().Next(0, 490))

    End Sub
    Dim score As Integer = 0
    Private Sub Timer1_Tick(sender As Object, e As EventArgs) Handles Timer1.Tick
        Label1.Text = score
        If snake.Bounds.IntersectsWith(apple.Bounds) Then
            snake.Height += 10
            snake.Width += 10
            score += 1
            apple.Location = New Point(New Random().Next(0, 490), New Random().Next(0, 490))
        End If
    End Sub

    Private Sub Timer2_Tick(sender As Object, e As EventArgs) Handles Timer2.Tick
        If score = 101 Then
            Timer1.Stop()
            Timer2.Stop()
            MessageBox.Show("Вы прошли игру!")
            Application.Exit()
        End If
    End Sub
End Class
